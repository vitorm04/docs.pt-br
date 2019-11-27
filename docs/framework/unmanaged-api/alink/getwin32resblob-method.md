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
ms.openlocfilehash: ff3103a46390c880a56ff443bfe20744f2ba0bfd
ms.sourcegitcommit: 9a39f2a06f110c9c7ca54ba216900d038aa14ef3
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/23/2019
ms.locfileid: "74430694"
---
# <a name="getwin32resblob-method"></a><span data-ttu-id="a4211-102">Método GetWin32ResBlob</span><span class="sxs-lookup"><span data-stu-id="a4211-102">GetWin32ResBlob Method</span></span>
<span data-ttu-id="a4211-103">Recupera o blob de recursos do Win32.</span><span class="sxs-lookup"><span data-stu-id="a4211-103">Retrieves Win32 resource blob.</span></span> <span data-ttu-id="a4211-104">Chame esse método depois de definir as opções de assembly.</span><span class="sxs-lookup"><span data-stu-id="a4211-104">Call this method after setting assembly options.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="a4211-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="a4211-105">Syntax</span></span>  
  
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
  
## <a name="parameters"></a><span data-ttu-id="a4211-106">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="a4211-106">Parameters</span></span>  
 `AssemblyID`  
 <span data-ttu-id="a4211-107">ID do assembly.</span><span class="sxs-lookup"><span data-stu-id="a4211-107">ID of the assembly.</span></span>  
  
 `FileToken`  
 <span data-ttu-id="a4211-108">O token de arquivo usado para recuperar o nome de o FileName a ser usado ao construir o recurso de versão do Win32</span><span class="sxs-lookup"><span data-stu-id="a4211-108">File token used to retrieve the filename to be used when constructing the Win32 Version resource</span></span>  
  
 `fDll`  
 <span data-ttu-id="a4211-109">TRUE se o arquivo for uma DLL, false para um EXE.</span><span class="sxs-lookup"><span data-stu-id="a4211-109">TRUE if file is a DLL, false for an EXE.</span></span>  
  
 `pszIconFile`  
 <span data-ttu-id="a4211-110">Ícone opcional para inserir no blob de recursos.</span><span class="sxs-lookup"><span data-stu-id="a4211-110">Optional icon to insert into the resource blob.</span></span>  
  
 `ppResBlob`  
 <span data-ttu-id="a4211-111">Recebe o blob de recursos.</span><span class="sxs-lookup"><span data-stu-id="a4211-111">Receives the resource blob.</span></span>  
  
 `pcbResBlob`  
 <span data-ttu-id="a4211-112">Recebe o tamanho do blob.</span><span class="sxs-lookup"><span data-stu-id="a4211-112">Receives the size of the blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="a4211-113">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="a4211-113">Return Value</span></span>  
 <span data-ttu-id="a4211-114">Retorna S_OK se o método tiver sucesso.</span><span class="sxs-lookup"><span data-stu-id="a4211-114">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="a4211-115">Requisitos</span><span class="sxs-lookup"><span data-stu-id="a4211-115">Requirements</span></span>  
 <span data-ttu-id="a4211-116">Requer ALink. h</span><span class="sxs-lookup"><span data-stu-id="a4211-116">Requires alink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4211-117">Consulte também</span><span class="sxs-lookup"><span data-stu-id="a4211-117">See also</span></span>

- [<span data-ttu-id="a4211-118">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="a4211-118">IALink Interface</span></span>](ialink-interface.md)
- [<span data-ttu-id="a4211-119">Interface IALink2</span><span class="sxs-lookup"><span data-stu-id="a4211-119">IALink2 Interface</span></span>](ialink2-interface.md)
- [<span data-ttu-id="a4211-120">API do ALink</span><span class="sxs-lookup"><span data-stu-id="a4211-120">ALink API</span></span>](index.md)
