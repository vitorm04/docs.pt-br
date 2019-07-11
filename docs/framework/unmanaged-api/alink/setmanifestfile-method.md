---
title: Método SetManifestFile
ms.date: 03/30/2017
api_name:
- IALink3.SetManifestFile
api_location:
- alink.dll
api_type:
- COM
f1_keywords:
- SetManifestFile
helpviewer_keywords:
- SetManifestFile method
ms.assetid: 1b33de4c-19cb-4a36-a93f-8675b2a36d58
topic_type:
- apiref
author: mairaw
ms.author: mairaw
ms.openlocfilehash: 825bb945e0d8662a4dadc9d688de6a677165df4a
ms.sourcegitcommit: 7f616512044ab7795e32806578e8dc0c6a0e038f
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 07/10/2019
ms.locfileid: "67741475"
---
# <a name="setmanifestfile-method"></a><span data-ttu-id="4ff77-102">Método SetManifestFile</span><span class="sxs-lookup"><span data-stu-id="4ff77-102">SetManifestFile Method</span></span>
<span data-ttu-id="4ff77-103">Permite que você especificar ou redefinir o arquivo de manifesto que o vinculador usa quando cria o assembly.</span><span class="sxs-lookup"><span data-stu-id="4ff77-103">Enables you to specify or reset the manifest file that the linker uses when it creates the assembly.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4ff77-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="4ff77-104">Syntax</span></span>  
  
```cpp  
HRESULT SetManifestFile(  
    LPCWSTR pszFile  
) PURE;  
```  
  
## <a name="parameters"></a><span data-ttu-id="4ff77-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="4ff77-105">Parameters</span></span>  
 `pszFile`  
  
 <span data-ttu-id="4ff77-106">O nome do arquivo de manifesto cujos conteúdos são colocados no blob de recursos do Win32.</span><span class="sxs-lookup"><span data-stu-id="4ff77-106">The name of the manifest file whose contents are put into the Win32 resources blob.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="4ff77-107">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="4ff77-107">Return Value</span></span>  
 <span data-ttu-id="4ff77-108">Se o método for bem-sucedido, retornará S_OK.</span><span class="sxs-lookup"><span data-stu-id="4ff77-108">Returns S_OK if the method succeeds.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4ff77-109">Comentários</span><span class="sxs-lookup"><span data-stu-id="4ff77-109">Remarks</span></span>  
 <span data-ttu-id="4ff77-110">Chame isso antes de solicitar o Win32ResBlob.</span><span class="sxs-lookup"><span data-stu-id="4ff77-110">Call this before asking for the Win32ResBlob.</span></span> <span data-ttu-id="4ff77-111">O valor da `pszFile` parâmetro é o nome do arquivo de manifesto cujos conteúdos são lidos e put nos recursos do Win32 com ID de RT_MANIFEST.</span><span class="sxs-lookup"><span data-stu-id="4ff77-111">The value of the `pszFile` parameter is the name of the manifest file whose contents are read and put in the Win32 resources with ID of RT_MANIFEST.</span></span> <span data-ttu-id="4ff77-112">Quando chamado usando um parâmetro de NULL, nenhum manifesto lida anteriormente está desmarcado.</span><span class="sxs-lookup"><span data-stu-id="4ff77-112">When called by using a parameter of NULL, any previously read manifest is cleared.</span></span> <span data-ttu-id="4ff77-113">Isso permite que um para redefinir o estado do vinculador para que o tempo de inicialização.</span><span class="sxs-lookup"><span data-stu-id="4ff77-113">This enables one to reset the state of the linker to that of initialization time.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="4ff77-114">Requisitos</span><span class="sxs-lookup"><span data-stu-id="4ff77-114">Requirements</span></span>  
 <span data-ttu-id="4ff77-115">Requer aLink.h</span><span class="sxs-lookup"><span data-stu-id="4ff77-115">Requires aLink.h</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4ff77-116">Consulte também</span><span class="sxs-lookup"><span data-stu-id="4ff77-116">See also</span></span>

- [<span data-ttu-id="4ff77-117">Interface IALink3</span><span class="sxs-lookup"><span data-stu-id="4ff77-117">IALink3 Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink3-interface.md)
- [<span data-ttu-id="4ff77-118">API do ALink</span><span class="sxs-lookup"><span data-stu-id="4ff77-118">ALink API</span></span>](../../../../docs/framework/unmanaged-api/alink/index.md)
- [<span data-ttu-id="4ff77-119">Interface IALink</span><span class="sxs-lookup"><span data-stu-id="4ff77-119">IALink Interface</span></span>](../../../../docs/framework/unmanaged-api/alink/ialink-interface.md)
- [<span data-ttu-id="4ff77-120">Al.exe (Assembly Linker)</span><span class="sxs-lookup"><span data-stu-id="4ff77-120">Al.exe (Assembly Linker)</span></span>](../../../../docs/framework/tools/al-exe-assembly-linker.md)
