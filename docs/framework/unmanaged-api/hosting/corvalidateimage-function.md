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
ms.openlocfilehash: 3a6da0e845fa50d090cdf0808b211a5806c40961
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79178211"
---
# <a name="_corvalidateimage-function"></a><span data-ttu-id="3b712-102">Função _CorValidateImage</span><span class="sxs-lookup"><span data-stu-id="3b712-102">_CorValidateImage Function</span></span>
<span data-ttu-id="3b712-103">Valida imagens gerenciadas do módulo e notifica o carregador do sistema operacional depois de carregado.</span><span class="sxs-lookup"><span data-stu-id="3b712-103">Validates managed module images, and notifies the operating system loader after they have been loaded.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="3b712-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="3b712-104">Syntax</span></span>  
  
```cpp  
STDAPI _CorValidateImage (
   [in] PVOID* ImageBase,  
   [in] LPCWSTR FileName  
);  
```  
  
## <a name="parameters"></a><span data-ttu-id="3b712-105">parâmetros</span><span class="sxs-lookup"><span data-stu-id="3b712-105">Parameters</span></span>  
 `ImageBase`  
 <span data-ttu-id="3b712-106">[em] Um ponteiro para o local de partida da imagem para validar como código gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3b712-106">[in] A pointer to the starting location of the image to validate as managed code.</span></span> <span data-ttu-id="3b712-107">A imagem já deve ser carregada na memória.</span><span class="sxs-lookup"><span data-stu-id="3b712-107">The image must already be loaded into memory.</span></span>  
  
 `FileName`  
 <span data-ttu-id="3b712-108">[em] O nome do arquivo da imagem.</span><span class="sxs-lookup"><span data-stu-id="3b712-108">[in] The file name of the image.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="3b712-109">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3b712-109">Return Value</span></span>  
 <span data-ttu-id="3b712-110">Esta função retorna `E_INVALIDARG`os `E_OUTOFMEMORY` `E_UNEXPECTED`valores `E_FAIL`padrão, e , bem como os seguintes valores.</span><span class="sxs-lookup"><span data-stu-id="3b712-110">This function returns the standard values `E_INVALIDARG`, `E_OUTOFMEMORY`, `E_UNEXPECTED`, and `E_FAIL`, as well as the following values.</span></span>  
  
|<span data-ttu-id="3b712-111">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="3b712-111">Return value</span></span>|<span data-ttu-id="3b712-112">Descrição</span><span class="sxs-lookup"><span data-stu-id="3b712-112">Description</span></span>|  
|------------------|-----------------|  
|`STATUS_INVALID_IMAGE_FORMAT`|<span data-ttu-id="3b712-113">A imagem é inválida.</span><span class="sxs-lookup"><span data-stu-id="3b712-113">The image is invalid.</span></span> <span data-ttu-id="3b712-114">Este valor tem o HRESULT 0xC0000007BL.</span><span class="sxs-lookup"><span data-stu-id="3b712-114">This value has the HRESULT 0xC000007BL.</span></span>|  
|`STATUS_SUCCESS`|<span data-ttu-id="3b712-115">A imagem é válida.</span><span class="sxs-lookup"><span data-stu-id="3b712-115">The image is valid.</span></span> <span data-ttu-id="3b712-116">Este valor tem o HRESULT 0x0000000L.</span><span class="sxs-lookup"><span data-stu-id="3b712-116">This value has the HRESULT 0x00000000L.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="3b712-117">Comentários</span><span class="sxs-lookup"><span data-stu-id="3b712-117">Remarks</span></span>  
 <span data-ttu-id="3b712-118">Nas versões Windows XP e posteriores, o carregador do sistema operacional verifica os módulos gerenciados examinando o bit Com Dscriptor Directory no cabeçalho coff (formato de arquivo de objeto comum).</span><span class="sxs-lookup"><span data-stu-id="3b712-118">In Windows XP and later versions, the operating system loader checks for managed modules by examining the COM Descriptor Directory bit in the common object file format (COFF) header.</span></span> <span data-ttu-id="3b712-119">Um bit definido indica um módulo gerenciado.</span><span class="sxs-lookup"><span data-stu-id="3b712-119">A set bit indicates a managed module.</span></span> <span data-ttu-id="3b712-120">Se o carregador detectar um módulo gerenciado, ele carregará MsCorEE.dll e chamadas, `_CorValidateImage`o que executa as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="3b712-120">If the loader detects a managed module, it loads MsCorEE.dll and calls `_CorValidateImage`, which performs the following actions:</span></span>  
  
- <span data-ttu-id="3b712-121">Confirma que a imagem é um módulo gerenciado válido.</span><span class="sxs-lookup"><span data-stu-id="3b712-121">Confirms that the image is a valid managed module.</span></span>  
  
- <span data-ttu-id="3b712-122">Altera o ponto de entrada na imagem para um ponto de entrada no tempo de execução do idioma comum (CLR).</span><span class="sxs-lookup"><span data-stu-id="3b712-122">Changes the entry point in the image to an entry point in the common language runtime (CLR).</span></span>  
  
- <span data-ttu-id="3b712-123">Para versões de 64 bits do Windows, modifica a imagem que está na memória, transformando-a do formato PE32 para PE32+.</span><span class="sxs-lookup"><span data-stu-id="3b712-123">For 64-bit versions of Windows, modifies the image that is in memory by transforming it from PE32 to PE32+ format.</span></span>  
  
- <span data-ttu-id="3b712-124">Retorna ao carregador quando as imagens do módulo gerenciado forem carregadas.</span><span class="sxs-lookup"><span data-stu-id="3b712-124">Returns to the loader when the managed module images are loaded.</span></span>  
  
 <span data-ttu-id="3b712-125">Para imagens executáveis, o carregador do sistema operacional então chama a função [_CorExeMain,](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) independentemente do ponto de entrada especificado no executável.</span><span class="sxs-lookup"><span data-stu-id="3b712-125">For executable images, the operating system loader then calls the [_CorExeMain](../../../../docs/framework/unmanaged-api/hosting/corexemain-function.md) function, regardless of the entry point specified in the executable.</span></span> <span data-ttu-id="3b712-126">Para imagens de montagem DLL, o carregador chama a função [_CorDllMain.](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md)</span><span class="sxs-lookup"><span data-stu-id="3b712-126">For DLL assembly images, the loader calls the [_CorDllMain](../../../../docs/framework/unmanaged-api/hosting/cordllmain-function.md) function.</span></span>  
  
 <span data-ttu-id="3b712-127">`_CorExeMain`ou `_CorDllMain` executa as seguintes ações:</span><span class="sxs-lookup"><span data-stu-id="3b712-127">`_CorExeMain` or `_CorDllMain` performs the following actions:</span></span>  
  
- <span data-ttu-id="3b712-128">Inicializa a CLR.</span><span class="sxs-lookup"><span data-stu-id="3b712-128">Initializes the CLR.</span></span>  
  
- <span data-ttu-id="3b712-129">Localiza o ponto de entrada gerenciado a partir do cabeçalho CLR da montagem.</span><span class="sxs-lookup"><span data-stu-id="3b712-129">Locates the managed entry point from the assembly's CLR header.</span></span>  
  
- <span data-ttu-id="3b712-130">Começa a execução.</span><span class="sxs-lookup"><span data-stu-id="3b712-130">Begins execution.</span></span>  
  
 <span data-ttu-id="3b712-131">O carregador chama a função [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) quando as imagens do módulo gerenciadas são descarregadas.</span><span class="sxs-lookup"><span data-stu-id="3b712-131">The loader calls the [_CorImageUnloading](../../../../docs/framework/unmanaged-api/hosting/corimageunloading-function.md) function when managed module images are unloaded.</span></span> <span data-ttu-id="3b712-132">No entanto, essa função não realiza nenhuma ação; ele só retorna.</span><span class="sxs-lookup"><span data-stu-id="3b712-132">However, this function does not perform any action; it just returns.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="3b712-133">Requisitos</span><span class="sxs-lookup"><span data-stu-id="3b712-133">Requirements</span></span>  
 <span data-ttu-id="3b712-134">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="3b712-134">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="3b712-135">**Cabeçalho:** Cor.h</span><span class="sxs-lookup"><span data-stu-id="3b712-135">**Header:** Cor.h</span></span>  
  
 <span data-ttu-id="3b712-136">**Biblioteca:** Incluído como um recurso em MsCorEE.dll</span><span class="sxs-lookup"><span data-stu-id="3b712-136">**Library:** Included as a resource in MsCorEE.dll</span></span>  
  
 <span data-ttu-id="3b712-137">**.NET Framework Versions:**[!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="3b712-137">**.NET Framework Versions:** [!INCLUDE[net_current_v10plus](../../../../includes/net-current-v10plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="3b712-138">Confira também</span><span class="sxs-lookup"><span data-stu-id="3b712-138">See also</span></span>

- [<span data-ttu-id="3b712-139">Funções estáticas globais de metadados</span><span class="sxs-lookup"><span data-stu-id="3b712-139">Metadata Global Static Functions</span></span>](../../../../docs/framework/unmanaged-api/metadata/metadata-global-static-functions.md)
