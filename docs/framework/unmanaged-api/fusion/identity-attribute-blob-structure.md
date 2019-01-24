---
title: Estrutura IDENTITY_ATTRIBUTE_BLOB
ms.date: 03/30/2017
dev_langs:
- cpp
api_name:
- IDENTITY_ATTRIBUTE_BLOB
api_location:
- fusion.dll
api_type:
- COM
f1_keywords:
- IDENTITY_ATTRIBUTE_BLOB
helpviewer_keywords:
- IDENTITY_ATTRIBUTE_BLOB structure [.NET Framework fusion]
ms.assetid: af14ae5f-d226-47dd-ba90-8fc6e6605d4d
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: eb2c560f8f906f20de752e5dfad995e2082caaea
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54654666"
---
# <a name="identityattributeblob-structure"></a><span data-ttu-id="7e2ef-102">Estrutura IDENTITY_ATTRIBUTE_BLOB</span><span class="sxs-lookup"><span data-stu-id="7e2ef-102">IDENTITY_ATTRIBUTE_BLOB Structure</span></span>
<span data-ttu-id="7e2ef-103">Contém informações sobre um único atributo em um assembly e consiste em três `DWORD`s.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-103">Contains information about a single attribute in an assembly, and consists of three `DWORD`s.</span></span> <span data-ttu-id="7e2ef-104">Cada `DWORD` é um deslocamento em um buffer de caracteres produzido pela `CurrentIntoBuffer` método o [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) interface</span><span class="sxs-lookup"><span data-stu-id="7e2ef-104">Each `DWORD` is an offset into a character buffer produced by the `CurrentIntoBuffer` method of the [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md) interface</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7e2ef-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7e2ef-105">Syntax</span></span>  
  
```  
typedef struct _IDENTITY_ATTRIBUTE_BLOB {  
    DWORD  ofsNamespace;  
    DWORD  ofsName;  
    DWORD  ofsValue;  
}   IDENTITY_ATTRIBUTE_BLOB;  
```  
  
## <a name="members"></a><span data-ttu-id="7e2ef-106">Membros</span><span class="sxs-lookup"><span data-stu-id="7e2ef-106">Members</span></span>  
  
|<span data-ttu-id="7e2ef-107">Membro</span><span class="sxs-lookup"><span data-stu-id="7e2ef-107">Member</span></span>|<span data-ttu-id="7e2ef-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="7e2ef-108">Description</span></span>|  
|------------|-----------------|  
|`ofsNamespace`|<span data-ttu-id="7e2ef-109">O primeiro deslocamento no buffer de caractere.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-109">The first offset into the character buffer.</span></span> <span data-ttu-id="7e2ef-110">Esse deslocamento não é seguido por namespace do atributo, mas por uma série de caracteres nulos.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-110">This offset is not followed by the attribute's namespace, but by a series of null characters.</span></span> <span data-ttu-id="7e2ef-111">Portanto, ele não é usado.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-111">Therefore, it is not used.</span></span>|  
|`ofsName`|<span data-ttu-id="7e2ef-112">O deslocamento segundo para o buffer de caracteres.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-112">The second offset into the character buffer.</span></span> <span data-ttu-id="7e2ef-113">Esse local marca o início do nome do atributo.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-113">This location marks the start of the attribute's name.</span></span>|  
|`ofsValue`|<span data-ttu-id="7e2ef-114">O terceiro deslocamento no buffer de caractere.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-114">The third offset into the character buffer.</span></span> <span data-ttu-id="7e2ef-115">Esse local marca o início do valor do atributo.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-115">This location marks the start of the attribute's value.</span></span>|  
  
## <a name="sample"></a><span data-ttu-id="7e2ef-116">Amostra</span><span class="sxs-lookup"><span data-stu-id="7e2ef-116">Sample</span></span>  
 <span data-ttu-id="7e2ef-117">O exemplo a seguir ilustra várias etapas básicas, que acaba resultam em um populados `IDENTITY_ATTRIBUTE_BLOB` estrutura:</span><span class="sxs-lookup"><span data-stu-id="7e2ef-117">The following example illustrates several basic steps, which eventually result in a populated `IDENTITY_ATTRIBUTE_BLOB` structure:</span></span>  
  
1.  <span data-ttu-id="7e2ef-118">Obter um [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) para o assembly.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-118">Obtain an [IReferenceIdentity](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md) for the assembly.</span></span>  
  
2.  <span data-ttu-id="7e2ef-119">Chame o `IReferenceIdentity::EnumAttributes` método e obter uma [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7e2ef-119">Call the `IReferenceIdentity::EnumAttributes` method, and obtain an [IEnumIDENTITY_ATTRIBUTE](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md).</span></span>  
  
3.  <span data-ttu-id="7e2ef-120">Criar um buffer de caracteres e convertê-la como um `IDENTITY_ATTRIBUTE_BLOB` estrutura.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-120">Create a character buffer, and cast it as an `IDENTITY_ATTRIBUTE_BLOB` structure.</span></span>  
  
4.  <span data-ttu-id="7e2ef-121">Chame o `CurrentIntoBuffer` método da `IEnumIDENTITY_ATTRIBUTE` interface.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-121">Call the `CurrentIntoBuffer` method of the `IEnumIDENTITY_ATTRIBUTE` interface.</span></span> <span data-ttu-id="7e2ef-122">Esse método copia os atributos `Namespace`, `Name`, e `Value` no buffer de caractere.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-122">This method copies the attributes `Namespace`, `Name`, and `Value` into the character buffer.</span></span> <span data-ttu-id="7e2ef-123">Os deslocamentos de três para essas cadeias de caracteres serão disponibilizadas no `IDENTITY_ATTRIBUTE_BLOB` estrutura.</span><span class="sxs-lookup"><span data-stu-id="7e2ef-123">The three offsets to those strings will become available in the `IDENTITY_ATTRIBUTE_BLOB` structure.</span></span>  
  
```  
// EnumAssemblyAttributes.cpp : main project file.  
  
#include "stdafx.h"  
  
#include "fusion.h"  
#include "windows.h"  
#include "stdio.h"  
#include "mscoree.h"  
#include "isolation.h"  
  
typedef HRESULT (__stdcall *PFNGETREF)(LPCWSTR pwzFile, REFIID riid, IUnknown **ppUnk);  
typedef HRESULT (__stdcall *PFNGETAUTH)(IIdentityAuthority **ppIIdentityAuthority);  
  
PFNGETREF                   g_pfnGetAssemblyIdentityFromFile = NULL;  
PFNGETAUTH                  g_pfnGetIdentityAuthority = NULL;  
IUnknown                    *g_pUnk = NULL;  
  
bool Init()  
{  
    HRESULT     hr = S_OK;  
    DWORD       dwSize = 0;  
    bool        bRC = false;  
  
    hr = CorBindToRuntimeEx(NULL, L"wks", 0, CLSID_CorRuntimeHost,  
                           IID_ICorRuntimeHost, (void **)&g_pUnk);  
    if(FAILED(hr)) {  
        printf("Error: Failed to initialize CLR runtime! hr = 0x%0x\n",  
                hr);  
        goto Exit;  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetAssemblyIdentityFromFile",  
                         (VOID **)&g_pfnGetAssemblyIdentityFromFile);  
    }  
  
    if (SUCCEEDED(hr)) {  
        hr = GetRealProcAddress("GetIdentityAuthority",  
                                (VOID **)&g_pfnGetIdentityAuthority);  
    }  
  
    if (!g_pfnGetAssemblyIdentityFromFile ||   
        !g_pfnGetIdentityAuthority)  
    {  
        printf("Error: Cannot get required APIs from fusion.dll!\n");  
        goto Exit;  
    }  
  
    bRC = true;  
  
Exit:  
    return bRC;  
}  
  
void Shutdown()  
{  
    if(g_pUnk) {  
        g_pUnk->Release();  
        g_pUnk = NULL;  
    }  
}  
  
void Usage()  
{  
    printf("EnumAssemblyAttributes: A tool to enumerate the identity   
            attributes of a given assembly.\n\n");  
    printf("Usage: EnumAssemblyAttributes AssemblyFilePath\n");  
    printf("\n");  
}  
  
int _cdecl wmain(int argc, LPCWSTR argv[])  
{  
    int     iResult = 1;  
    IUnknown                    *pUnk  = NULL;  
    IReferenceIdentity          *pRef  = NULL;  
    HRESULT                     hr     = S_OK;     
    IEnumIDENTITY_ATTRIBUTE     *pEnum = NULL;  
    BYTE                        abData[1024];  
    DWORD                       cbAvailable;  
    DWORD                       cbUsed;  
    IDENTITY_ATTRIBUTE_BLOB     *pBlob;  
  
    if(argc != 2) {  
        Usage();  
        goto Exit;  
    }  
  
    if(!Init()) {  
        printf("Failure initializing EnumIdAttr.\n");  
        goto Exit;  
    }  
  
    hr = g_pfnGetAssemblyIdentityFromFile(argv[1],   
                            __uuidof(IReferenceIdentity), &pUnk);  
  
    if (FAILED(hr)) {  
        printf("GetAssemblyIdentityFromFile failed with hr = 0x%x",   
                hr);  
        goto Exit;  
    }  
  
    hr = pUnk->QueryInterface(__uuidof(IReferenceIdentity),   
                              (void**)&pRef);  
    if (FAILED(hr)) {  
        goto Exit;  
    }  
  
    hr = pRef->EnumAttributes(&pEnum);  
    if (FAILED(hr)) {  
        printf("IReferenceIdentity::EnumAttributes failed with hr =   
                0x%x", hr);  
        goto Exit;  
    }  
  
    pBlob = (IDENTITY_ATTRIBUTE_BLOB *)(abData);  
    while (1) {  
        cbAvailable = sizeof(abData);  
        hr = pEnum->CurrentIntoBuffer(cbAvailable, abData, &cbUsed);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::CurrentIntoBuffer failed   
                    with hr = 0x%x", hr);  
            goto Exit;  
        }  
  
        if (! cbUsed) {  
            break;  
        }  
  
        LPWSTR pwzNameSpace = (LPWSTR)(abData + pBlob->ofsNamespace);  
        LPWSTR pwzName      = (LPWSTR)(abData + pBlob->ofsName);  
        LPWSTR pwzValue     = (LPWSTR)(abData + pBlob->ofsValue);  
        printf("%ws: %ws = %ws\n", pwzNameSpace, pwzName, pwzValue);  
  
        hr = pEnum->Skip(1);  
        if (FAILED(hr)) {  
            printf("IEnumIDENTITY_ATTRIBUTE::Skip failed with hr =   
                    0x%x", hr);  
            goto Exit;  
        }  
    }  
  
    iResult = 0;  
  
Exit:  
  
    Shutdown();  
  
    if (pUnk) {  
        pUnk->Release();  
    }  
  
    if (pRef) {  
        pRef->Release();  
    }  
  
    if (pEnum) {  
        pEnum->Release();  
    }  
  
    return iResult;  
}  
```  
  
### <a name="to-run-the-sample"></a><span data-ttu-id="7e2ef-124">Para executar a amostra</span><span class="sxs-lookup"><span data-stu-id="7e2ef-124">To run the sample</span></span>  
 <span data-ttu-id="7e2ef-125">C:\\> EnumAssemblyAttributes.exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll</span><span class="sxs-lookup"><span data-stu-id="7e2ef-125">C:\\> EnumAssemblyAttributes.exe C:\WINDOWS\Microsoft.NET\Framework\v2.0.50727\System.dll</span></span>  
  
### <a name="sample-output"></a><span data-ttu-id="7e2ef-126">Saída de exemplo</span><span class="sxs-lookup"><span data-stu-id="7e2ef-126">Sample output</span></span>  
 <span data-ttu-id="7e2ef-127">Cultura = neutral</span><span class="sxs-lookup"><span data-stu-id="7e2ef-127">Culture = neutral</span></span>  
  
 <span data-ttu-id="7e2ef-128">nome = sistema</span><span class="sxs-lookup"><span data-stu-id="7e2ef-128">name = System</span></span>  
  
 <span data-ttu-id="7e2ef-129">processorArchitecture = MSIL</span><span class="sxs-lookup"><span data-stu-id="7e2ef-129">processorArchitecture = MSIL</span></span>  
  
 <span data-ttu-id="7e2ef-130">PublicKeyToken = b77a5c561934e089</span><span class="sxs-lookup"><span data-stu-id="7e2ef-130">PublicKeyToken = b77a5c561934e089</span></span>  
  
 <span data-ttu-id="7e2ef-131">Versão = 2.0.0.0</span><span class="sxs-lookup"><span data-stu-id="7e2ef-131">Version = 2.0.0.0</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7e2ef-132">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7e2ef-132">Requirements</span></span>  
 <span data-ttu-id="7e2ef-133">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7e2ef-133">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7e2ef-134">**Cabeçalho:** Isolation.h</span><span class="sxs-lookup"><span data-stu-id="7e2ef-134">**Header:** Isolation.h</span></span>  
  
 <span data-ttu-id="7e2ef-135">**Versões do .NET Framework:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="7e2ef-135">**.NET Framework Versions:** [!INCLUDE[net_current_v20plus](../../../../includes/net-current-v20plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7e2ef-136">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7e2ef-136">See also</span></span>
- [<span data-ttu-id="7e2ef-137">Interface IReferenceIdentity</span><span class="sxs-lookup"><span data-stu-id="7e2ef-137">IReferenceIdentity Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ireferenceidentity-interface.md)
- [<span data-ttu-id="7e2ef-138">Interface IEnumIDENTITY_ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="7e2ef-138">IEnumIDENTITY_ATTRIBUTE Interface</span></span>](../../../../docs/framework/unmanaged-api/fusion/ienumidentity-attribute-interface.md)
- [<span data-ttu-id="7e2ef-139">Estrutura IDENTITY_ATTRIBUTE</span><span class="sxs-lookup"><span data-stu-id="7e2ef-139">IDENTITY_ATTRIBUTE Structure</span></span>](../../../../docs/framework/unmanaged-api/fusion/identity-attribute-structure.md)
- [<span data-ttu-id="7e2ef-140">Estruturas de fusão</span><span class="sxs-lookup"><span data-stu-id="7e2ef-140">Fusion Structures</span></span>](../../../../docs/framework/unmanaged-api/fusion/fusion-structures.md)
