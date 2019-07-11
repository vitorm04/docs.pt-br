---
title: Método GetWin32ResBlob
ms.date: 03/30/2017
api_name:
- IALink.GetWin32ResBlob
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- GetWin32ResBlob
helpviewer_keywords:
- GetWin32ResBlob method
ms.assetid: 36997e04-f9f6-4254-a041-6767ac6c51d9
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: bdc1ef6490f250ebe93b0482adf244adfc0ffd56
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741790"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="043e5-102">Método GetWin32ResBlob</span><span class="sxs-lookup"><span data-stu-id="043e5-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="043e5-103">Recupera o blob de recurso do Win32.</span><span class="sxs-lookup"><span data-stu-id="043e5-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="043e5-104">Chame esse método depois de definir as opções de assembly.</span><span class="sxs-lookup"><span data-stu-id="043e5-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="043e5-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="043e5-105">Syntax</span></span>  
  
```cpp  
HRESULT GetWin32ResBlob(  
    mdAssembly    AssemblyID,  
    mdToken       FileToken,  
    BOOL          fDll,  
    LPCWSTR       pszIconFile,  
    const void**  ppResBlob,  
    DWORD*        pcbResBlob  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="043e5-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="043e5-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="043e5-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="043e5-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="043e5-108">Token de arquivo usado para recuperar o nome do arquivo a ser usado ao construir o recurso de versão do Win32</span><span class="sxs-lookup"><span data-stu-id="043e5-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="043e5-109">TRUE se o arquivo é uma DLL, false para que um EXE.</span><span class="sxs-lookup"><span data-stu-id="043e5-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="043e5-110">Ícone opcional para inserir no blob de recurso.</span><span class="sxs-lookup"><span data-stu-id="043e5-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="043e5-111">Recebe o blob de recurso.</span><span class="sxs-lookup"><span data-stu-id="043e5-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="043e5-112">Recebe o tamanho do blob.</span><span class="sxs-lookup"><span data-stu-id="043e5-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="043e5-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="043e5-113">Return Value</span></span>  
 <span data-ttu-id="043e5-114">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="043e5-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="043e5-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="043e5-115">Requirements</span></span>  
 <span data-ttu-id="043e5-116">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="043e5-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="043e5-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="043e5-117">See also</span></span>

- [<span data-ttu-id="043e5-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="043e5-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="043e5-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="043e5-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)
- [<span data-ttu-id="043e5-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="043e5-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
