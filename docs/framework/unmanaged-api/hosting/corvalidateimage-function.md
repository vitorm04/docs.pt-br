---
title: Função _CorValidateImage
ms.date: 03/30/2017
api_name:
- _CorValidateImage
api_location:
- mscoree.dll
api_type:
- DLLExport
f1_keywords:
- _CorValidateImage
helpviewer_keywords:
- _CorValidateImage function [.NET Framework hosting]
ms.assetid: 0117e080-05f9-4772-885d-e1847230947c
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: df9cc0cc86237b1ec439a4ec4fa6a75429c416d9
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59111170"
---
# <a name="corvalidateimage-function"></a><span data-ttu-id="18f16-102">Função _CorValidateImage</span><span class="sxs-lookup"><span data-stu-id="18f16-102">_CorValidateImage Function</span></span>
<span data-ttu-id="18f16-103">Valida imagens de módulo gerenciado e notifica o carregador do sistema operacional, depois de eles terem sido carregados.</span><span class="sxs-lookup"><span data-stu-id="18f16-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="18f16-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="18f16-104">Syntax</span></span>  
  
```  
STDAPI _CorValidateImage (   
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="18f16-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="18f16-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="18f16-106">[in] Um ponteiro para o local inicial da imagem para validar que o código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="18f16-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="18f16-107">A imagem já deve ser carregada na memória.</span><span class="sxs-lookup"><span data-stu-id="18f16-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="18f16-108">[in] O nome do arquivo da imagem.</span><span class="sxs-lookup"><span data-stu-id="18f16-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="18f16-109">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="18f16-109">Return Value</span></span>  
 <span data-ttu-id="18f16-110">Essa função retorna os valores padrão `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, e `E_FAIL`, bem como os valores a seguir.</span><span class="sxs-lookup"><span data-stu-id="18f16-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="18f16-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="18f16-111">Return value</span></span>|<span data-ttu-id="18f16-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="18f16-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="18f16-113">A imagem é inválida.</span><span class="sxs-lookup"><span data-stu-id="18f16-113">The image is invalid.</span></span> <span data-ttu-id="18f16-114">Esse valor tem o 0xC000007BL HRESULT.</span><span class="sxs-lookup"><span data-stu-id="18f16-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="18f16-115">A imagem é válida.</span><span class="sxs-lookup"><span data-stu-id="18f16-115">The image is valid.</span></span> <span data-ttu-id="18f16-116">Esse valor tem o 0x00000000L HRESULT.</span><span class="sxs-lookup"><span data-stu-id="18f16-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="18f16-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="18f16-117">Remarks</span></span>  
 <span data-ttu-id="18f16-118">No Windows XP e versões posteriores, o carregador do sistema operacional verifica módulos gerenciados examinando o diretório de descritor COM bit no cabeçalho formato COFF.</span><span class="sxs-lookup"><span data-stu-id="18f16-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="18f16-119">Um bit definido indica que um módulo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="18f16-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="18f16-120">Se o carregador detecta um módulo gerenciado, ele carrega mscoree. dll e chamadas `_CorValidateImage`, que executa as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="18f16-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
-   <span data-ttu-id="18f16-121">Confirma que a imagem é um módulo gerenciado válido.</span><span class="sxs-lookup"><span data-stu-id="18f16-121">Confirms that the image is a valid managed module.</span></span>  
  
-   <span data-ttu-id="18f16-122">Altera o ponto de entrada na imagem para um ponto de entrada no common language runtime (CLR).</span><span class="sxs-lookup"><span data-stu-id="18f16-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
-   <span data-ttu-id="18f16-123">Para versões de 64 bits do Windows, modifica a imagem que está na memória transformando-a do formato PE32 para o formato PE32 +.</span><span class="sxs-lookup"><span data-stu-id="18f16-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
-   <span data-ttu-id="18f16-124">Retorna o carregador quando as imagens de módulo gerenciado são carregadas.</span><span class="sxs-lookup"><span data-stu-id="18f16-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="18f16-125">Para imagens executáveis, o carregador do sistema operacional, em seguida, chama o [CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) função, independentemente do ponto de entrada especificado no executável.</span><span class="sxs-lookup"><span data-stu-id="18f16-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="18f16-126">Para imagens do assembly DLL, o carregador de chamadas a [cordllmain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) função.</span><span class="sxs-lookup"><span data-stu-id="18f16-126">For DLL assembly images, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="18f16-127">`_CorExeMain` ou `_CorDllMain` executa as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="18f16-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
-   <span data-ttu-id="18f16-128">Inicializa o CLR.</span><span class="sxs-lookup"><span data-stu-id="18f16-128">Initializes the CLR.</span></span>  
  
-   <span data-ttu-id="18f16-129">Localiza o ponto de entrada gerenciado de cabeçalho CLR do assembly.</span><span class="sxs-lookup"><span data-stu-id="18f16-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
-   <span data-ttu-id="18f16-130">Inicia a execução.</span><span class="sxs-lookup"><span data-stu-id="18f16-130">Begins execution.</span></span>  
  
 <span data-ttu-id="18f16-131">As chamadas de carregador a [CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) funcionar quando gerenciado imagens de módulo serão descarregadas.</span><span class="sxs-lookup"><span data-stu-id="18f16-131">The loader calls the [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="18f16-132">No entanto, essa função não executa nenhuma ação; ele simplesmente retorna.</span><span class="sxs-lookup"><span data-stu-id="18f16-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="18f16-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="18f16-133">Requirements</span></span>  
 <span data-ttu-id="18f16-134">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="18f16-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="18f16-135">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="18f16-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="18f16-136">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="18f16-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="18f16-137">**Versões do .NET Framework:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="18f16-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="18f16-138">Consulte também</span><span class="sxs-lookup"><span data-stu-id="18f16-138">See also</span></span>

- [<span data-ttu-id="18f16-139">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="18f16-139">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
