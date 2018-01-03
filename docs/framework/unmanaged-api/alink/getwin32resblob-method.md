---
title: "Método GetWin32ResBlob"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: IALink.GetWin32ResBlob
api_location: alink.dll
api_type: COM
f1_keywords: GetWin32ResBlob
helpviewer_keywords: GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type: apiref
caps.latest.revision: "5"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 5f09bfd3ccfd3ac37854d70c226f40b17f86ccf4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="f8a2e-102">Método GetWin32ResBlob</span><span class="sxs-lookup"><span data-stu-id="f8a2e-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="f8a2e-103">Recupera o blob de recursos do Win32.</span><span class="sxs-lookup"><span data-stu-id="f8a2e-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="f8a2e-104">Chame este método depois de definir opções de assembly.</span><span class="sxs-lookup"><span data-stu-id="f8a2e-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="f8a2e-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="f8a2e-105">Syntax</span></span>  
  
```  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
#### <a name="parameters"></a><span data-ttu-id="f8a2e-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="f8a2e-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="f8a2e-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="f8a2e-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="f8a2e-108">Token de arquivo usado para recuperar o nome do arquivo a ser usado ao construir o recurso da versão do Win32</span><span class="sxs-lookup"><span data-stu-id="f8a2e-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="f8a2e-109">TRUE se o arquivo é uma DLL, false para um executável.</span><span class="sxs-lookup"><span data-stu-id="f8a2e-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="f8a2e-110">Ícone opcional para inserir o blob de recurso.</span><span class="sxs-lookup"><span data-stu-id="f8a2e-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="f8a2e-111">Recebe o blob de recurso.</span><span class="sxs-lookup"><span data-stu-id="f8a2e-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="f8a2e-112">Recebe o tamanho do blob.</span><span class="sxs-lookup"><span data-stu-id="f8a2e-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="f8a2e-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="f8a2e-113">Return Value</span></span>  
 <span data-ttu-id="f8a2e-114">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="f8a2e-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="f8a2e-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="f8a2e-115">Requirements</span></span>  
 <span data-ttu-id="f8a2e-116">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="f8a2e-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f8a2e-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="f8a2e-117">See Also</span></span>  
 [<span data-ttu-id="f8a2e-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="f8a2e-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="f8a2e-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="f8a2e-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="f8a2e-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="f8a2e-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
