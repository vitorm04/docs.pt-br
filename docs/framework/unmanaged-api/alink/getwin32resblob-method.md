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
ms.openlocfilehash: f40b99c0a81bf0f2b622c7d23157dbb5736df1ca
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33403286"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="1056c-102">Método GetWin32ResBlob</span><span class="sxs-lookup"><span data-stu-id="1056c-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="1056c-103">Recupera o blob de recursos do Win32.</span><span class="sxs-lookup"><span data-stu-id="1056c-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="1056c-104">Chame este método depois de definir opções de assembly.</span><span class="sxs-lookup"><span data-stu-id="1056c-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="1056c-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="1056c-105">Syntax</span></span>  
  
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
  
#### <a name="parameters"></a><span data-ttu-id="1056c-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="1056c-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="1056c-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="1056c-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="1056c-108">Token de arquivo usado para recuperar o nome do arquivo a ser usado ao construir o recurso da versão do Win32</span><span class="sxs-lookup"><span data-stu-id="1056c-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="1056c-109">TRUE se o arquivo é uma DLL, false para um executável.</span><span class="sxs-lookup"><span data-stu-id="1056c-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="1056c-110">Ícone opcional para inserir o blob de recurso.</span><span class="sxs-lookup"><span data-stu-id="1056c-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="1056c-111">Recebe o blob de recurso.</span><span class="sxs-lookup"><span data-stu-id="1056c-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="1056c-112">Recebe o tamanho do blob.</span><span class="sxs-lookup"><span data-stu-id="1056c-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="1056c-113">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="1056c-113">Return Value</span></span>  
 <span data-ttu-id="1056c-114">Retorna S_OK se o método for bem-sucedido.</span><span class="sxs-lookup"><span data-stu-id="1056c-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="1056c-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="1056c-115">Requirements</span></span>  
 <span data-ttu-id="1056c-116">Requer alink.h</span><span class="sxs-lookup"><span data-stu-id="1056c-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1056c-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="1056c-117">See Also</span></span>  
 [<span data-ttu-id="1056c-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="1056c-118">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)  
 [<span data-ttu-id="1056c-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="1056c-119">IALink2 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink2-interface.md)  
 [<span data-ttu-id="1056c-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="1056c-120">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
