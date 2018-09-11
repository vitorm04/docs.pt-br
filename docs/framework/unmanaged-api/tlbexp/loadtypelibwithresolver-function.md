---
title: Função LoadTypeLibWithResolver
ms.date: 03/30/2017
api_name:
- LoadTypeLibWithResolver
api_location:
- TlbRef.dll
api_type:
- DLLExport
f1_keywords:
- LoadTypeLibWithResolver
helpviewer_keywords:
- LoadTypeLibWithResolver function [.NET Framework]
ms.assetid: 7123a89b-eb9b-463a-a552-a081e33b0a3a
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b6a217e2212bb900d7ba83ccdd9cb00d30454baf
ms.sourcegitcommit: 4b6490b2529707627ad77c3a43fbe64120397175
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/10/2018
ms.locfileid: "44264214"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="b8df5-102">Função LoadTypeLibWithResolver</span><span class="sxs-lookup"><span data-stu-id="b8df5-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="b8df5-103">Carrega uma biblioteca de tipos e usa fornecido [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) para resolver quaisquer bibliotecas de tipos referenciados internamente.</span><span class="sxs-lookup"><span data-stu-id="b8df5-103">Loads a type library and uses the supplied [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b8df5-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="b8df5-104">Syntax</span></span>  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="b8df5-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="b8df5-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="b8df5-106">[in] O caminho do arquivo da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="b8df5-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="b8df5-107">[in] Um [enumeração REGKIND](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind) sinalizador que controla como a biblioteca de tipos é registrada.</span><span class="sxs-lookup"><span data-stu-id="b8df5-107">[in] A [REGKIND enumeration](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/ne-oleauto-tagregkind) flag that controls how the type library is registered.</span></span> <span data-ttu-id="b8df5-108">Seus valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="b8df5-108">Its possible values are:</span></span>  
  
-   <span data-ttu-id="b8df5-109">`REGKIND_DEFAULT`: Use o comportamento de registro padrão.</span><span class="sxs-lookup"><span data-stu-id="b8df5-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
-   <span data-ttu-id="b8df5-110">`REGKIND_REGISTER`: Registre esta biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="b8df5-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
-   <span data-ttu-id="b8df5-111">`REGKIND_NONE`: Não registre a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="b8df5-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="b8df5-112">[in] Um ponteiro para a implementação de [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span><span class="sxs-lookup"><span data-stu-id="b8df5-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="b8df5-113">[out] Uma referência à biblioteca de tipos que está sendo carregada.</span><span class="sxs-lookup"><span data-stu-id="b8df5-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="b8df5-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="b8df5-114">Return Value</span></span>  
 <span data-ttu-id="b8df5-115">Um dos valores HRESULT listados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="b8df5-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="b8df5-116">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="b8df5-116">Return value</span></span>|<span data-ttu-id="b8df5-117">Significado</span><span class="sxs-lookup"><span data-stu-id="b8df5-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="b8df5-118">Êxito.</span><span class="sxs-lookup"><span data-stu-id="b8df5-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="b8df5-119">Sem memória.</span><span class="sxs-lookup"><span data-stu-id="b8df5-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="b8df5-120">Um ou mais dos ponteiros são inválidos.</span><span class="sxs-lookup"><span data-stu-id="b8df5-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="b8df5-121">Um ou mais argumentos são inválidos.</span><span class="sxs-lookup"><span data-stu-id="b8df5-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="b8df5-122">A função não pôde gravar no arquivo.</span><span class="sxs-lookup"><span data-stu-id="b8df5-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="b8df5-123">Não foi possível abrir o banco de dados de registro do sistema.</span><span class="sxs-lookup"><span data-stu-id="b8df5-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="b8df5-124">Não foi possível abrir a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="b8df5-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="b8df5-125">Não foi possível carregar a biblioteca de tipos ou DLL.</span><span class="sxs-lookup"><span data-stu-id="b8df5-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b8df5-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="b8df5-126">Remarks</span></span>  
 <span data-ttu-id="b8df5-127">O [Tlbexp.exe (exportador da biblioteca)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) chamadas a `LoadTypeLibWithResolver` função durante o processo de conversão de assembly para biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="b8df5-127">The [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="b8df5-128">Essa função carrega a biblioteca de tipo especificado com acesso mínimo ao registro.</span><span class="sxs-lookup"><span data-stu-id="b8df5-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="b8df5-129">A função, em seguida, examina a biblioteca de tipos para bibliotecas de tipos referenciados internamente, cada um deles deve ser carregada e adicionada à biblioteca de tipo de pai.</span><span class="sxs-lookup"><span data-stu-id="b8df5-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="b8df5-130">Antes de uma biblioteca de tipos referenciada pode ser carregada, seu caminho de arquivo de referência deve ser resolvido para um caminho de arquivo completo.</span><span class="sxs-lookup"><span data-stu-id="b8df5-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="b8df5-131">Isso é feito por meio do [método ResolveTypeLib](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) que é fornecido pela [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), que é passado a `pTlbResolver` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b8df5-131">This is accomplished through the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="b8df5-132">Quando o caminho completo do arquivo da biblioteca de tipos referenciada é conhecido, o `LoadTypeLibWithResolver` função carrega e adiciona a biblioteca de tipos referenciados na biblioteca de tipo pai, criando uma biblioteca de tipos mestre combinado.</span><span class="sxs-lookup"><span data-stu-id="b8df5-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="b8df5-133">Depois que a função resolve e carrega todas as bibliotecas de tipos referenciados internamente, ele retornará uma referência à biblioteca de tipo resolvidos mestre no `pptlib` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b8df5-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="b8df5-134">O `LoadTypeLibWithResolver` função geralmente é chamada pelo [Tlbexp.exe (exportador da biblioteca)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), que fornece seu próprio interno [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementação no `pTlbResolver` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="b8df5-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="b8df5-135">Se você chamar `LoadTypeLibWithResolver` diretamente, você deve fornecer seu próprio [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementação.</span><span class="sxs-lookup"><span data-stu-id="b8df5-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="b8df5-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="b8df5-136">Requirements</span></span>  
 <span data-ttu-id="b8df5-137">**Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="b8df5-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="b8df5-138">**Cabeçalho:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="b8df5-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="b8df5-139">**Biblioteca:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="b8df5-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="b8df5-140">**Versão do .NET framework:** 3.5, 3.0, 2.0</span><span class="sxs-lookup"><span data-stu-id="b8df5-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="b8df5-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="b8df5-141">See Also</span></span>  
 [<span data-ttu-id="b8df5-142">Funções auxiliares do Tlbexp</span><span class="sxs-lookup"><span data-stu-id="b8df5-142">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 [<span data-ttu-id="b8df5-143">Função LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="b8df5-143">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
