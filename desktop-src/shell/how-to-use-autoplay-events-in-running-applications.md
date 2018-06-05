---
Description: The IHWEventHandler interface can be registered in the running object table (ROT) so that running applications have access to AutoPlay events.
ms.assetid: 6FEFFB5D-DD8B-4FEA-B273-D32FC30CAFEA
title: How to Use AutoPlay Events in Running Applications
ms.technology: desktop
ms.prod: windows
ms.author: windowssdkdev
ms.topic: article
ms.date: 05/31/2018
---

# How to Use AutoPlay Events in Running Applications

The [**IHWEventHandler**](/windows/desktop/api/Shobjidl/nn-shobjidl-ihweventhandler) interface can be registered in the running object table (ROT) so that running applications have access to AutoPlay events.

The following instructions describe how to use AutoPlay events in running applications.

## Instructions

### Step 1:

Create a new component that implements the [**IHWEventHandler**](/windows/desktop/api/Shobjidl/nn-shobjidl-ihweventhandler) interface.

### Step 2:

Initialize the new component with the InitCmdLine value from the particular handler's entry under the **Handlers** key.

This step is required because Autoplay does not call the Initialize method.

### Step 3:

Call the [**CreateHardwareEventMoniker**](createhardwareeventmoniker.md) function to get a moniker that represents your component and the event handler that you want to call.

### Step 4:

Use the *ppmoniker* parameter to register your component in the ROT.

## Remarks

> [!Note]  
> [**LoadLibrary**](https://msdn.microsoft.com/windows/desktop/d936b4dd-058c-48e1-834b-b47ef6d8ef65) can pose security risks. Refer to the **LoadLibrary** documentation for information on how to correctly load DLLs with different versions of Windows.
>
> <span codelanguage=""></span>
>
> <table>
> <colgroup>
> <col style="width: 100%" />
> </colgroup>
> <tbody>
> <tr class="odd">
> <td><pre><code>typedef HRESULT (*CREATEHARDWAREEVENTMONIKER)(REFCLSID clsid, LPCWSTR pszEventHandler, IMoniker **ppmoniker);
>
> HRESULT RegisterComponent(IUnknown* punk, DWORD* dpwToken)
> {
>     HRESULT hr = E_FAIL;
>     HINSTANCE hinstShSvcs = LoadLibrary(TEXT(&quot;shsvcs.dll&quot;));
>     
>     if (hinstShSvcs)
>     {   
>         CREATEHARDWAREEVENTMONIKER fct = (CREATEHARDWAREEVENTMONIKER)GetProcAddress(hinstShSvcs, &quot;CreateHardwareEventMoniker&quot;);
>         if (fct)
>         {
>             IMoniker* pmoniker;
>             
>             hr = fct(CLSID_App, TEXT(&quot;VideoCameraArrival&quot;), &amp;pmoniker);
>
>             if (SUCCEEDED(hr))
>             {
>                 IRunningObjectTable *prot;
>                     
>                 if (SUCCEEDED(GetRunningObjectTable(0, &amp;prot)))
>                 {
>                     hr = prot-&gt;Register(ROTFLAGS_ALLOWANYCLIENT | ROTFLAGS_REGISTRATIONKEEPSALIVE, punk, pmoniker, &amp;amp;_dwRegisterROT);
>                     prot-&gt;Release();
>                 }
>                 pmoniker-&gt;Release();
>             }
>             CoRegisterClassObject(CLSID_App, static_cast&amp;lt;IClassFactory *&amp;gt;(this), CLSCTX_LOCAL_SERVER, REGCLS_MULTIPLEUSE, &amp;amp;_dwRegisterClass;
>         }
>         FreeLibrary(hinstShSvcs);
>     }
>     return hr;
> }
>                 </code></pre></td>
> </tr>
> </tbody>
> </table>
>
> 
>
>  
>
> The call to [**IRunningObjectTable::Register**](https://msdn.microsoft.com/windows/desktop/40f815b2-dfea-416c-aae1-7ba3a710ad91) requires that the component have the following **AppID** information in the registry.
>
> ```
> HKEY_CLASSES_ROOT
>    AppID
>       MyApp.exe
>          (Default) = MyApplication
>          AppID [REG_SZ] = {Your GUID here}
> ```
>
> ```
> HKEY_CLASSES_ROOT
>    AppID
>       {The same GUID here}
>          (Default) = MyApplication
>          RunAs = Interactive User
> ```
>
> ## Related topics
>
> <dl> <dt>

[**IHWEventHandler**](/windows/desktop/api/Shobjidl/nn-shobjidl-ihweventhandler)
</dt> <dt>

[**CreateHardwareEventMoniker**](createhardwareeventmoniker.md)
</dt> </dl>
>
>  
>
>  
>

