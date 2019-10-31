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
ms.openlocfilehash: 82fa0903474ee04b767fd9c68812efe7f0cc4fa0
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73124156"
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="cf8d8-102">Função LoadTypeLibWithResolver</span><span class="sxs-lookup"><span data-stu-id="cf8d8-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="cf8d8-103">Carrega uma biblioteca de tipos e usa a [interface ITypeLibResolver](itypelibresolver-interface.md) fornecida para resolver quaisquer bibliotecas de tipos referenciadas internamente.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-103">Loads a type library and uses the supplied [ITypeLibResolver interface](itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="cf8d8-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="cf8d8-104">Syntax</span></span>  
  
```cpp  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
## <a name="parameters"></a><span data-ttu-id="cf8d8-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="cf8d8-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="cf8d8-106">no O caminho do arquivo da biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="cf8d8-107">no Um sinalizador de [Enumeração regkind](https://docs.microsoft.com/windows/win32/api/oleauto/ne-oleauto-regkind) que controla como a biblioteca de tipos é registrada.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-107">[in] A [REGKIND enumeration](https://docs.microsoft.com/windows/win32/api/oleauto/ne-oleauto-regkind) flag that controls how the type library is registered.</span></span> <span data-ttu-id="cf8d8-108">Seus valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="cf8d8-108">Its possible values are:</span></span>  
  
- <span data-ttu-id="cf8d8-109">`REGKIND_DEFAULT`: usar o comportamento de registro padrão.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
- <span data-ttu-id="cf8d8-110">`REGKIND_REGISTER`: registre essa biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
- <span data-ttu-id="cf8d8-111">`REGKIND_NONE`: não Registre esta biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="cf8d8-112">no Um ponteiro para a implementação da [interface ITypeLibResolver](itypelibresolver-interface.md).</span><span class="sxs-lookup"><span data-stu-id="cf8d8-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="cf8d8-113">fora Uma referência à biblioteca de tipos que está sendo carregada.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="cf8d8-114">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="cf8d8-114">Return Value</span></span>  
 <span data-ttu-id="cf8d8-115">Um dos valores HRESULT listados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="cf8d8-116">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="cf8d8-116">Return value</span></span>|<span data-ttu-id="cf8d8-117">Significado</span><span class="sxs-lookup"><span data-stu-id="cf8d8-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="cf8d8-118">Êxito.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="cf8d8-119">Sem memória.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="cf8d8-120">Um ou mais ponteiros são inválidos.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="cf8d8-121">Um ou mais argumentos são inválidos.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="cf8d8-122">A função não pôde gravar no arquivo.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="cf8d8-123">Não foi possível abrir o banco de dados de registro do sistema.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="cf8d8-124">Não foi possível abrir a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="cf8d8-125">Não foi possível carregar a biblioteca de tipos ou a DLL.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="cf8d8-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="cf8d8-126">Remarks</span></span>  
 <span data-ttu-id="cf8d8-127">O [Tlbexp. exe (tipo de exportador da biblioteca de tipos)](../../tools/tlbexp-exe-type-library-exporter.md) chama a função `LoadTypeLibWithResolver` durante o processo de conversão assembly-to-Type-Library.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-127">The [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="cf8d8-128">Essa função carrega a biblioteca de tipos especificada com acesso mínimo ao registro.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="cf8d8-129">Em seguida, a função examina a biblioteca de tipos para bibliotecas de tipos referenciadas internamente, cada uma delas deve ser carregada e adicionada à biblioteca de tipos pai.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="cf8d8-130">Antes que uma biblioteca de tipos referenciada possa ser carregada, seu caminho de arquivo de referência deve ser resolvido para um caminho de arquivo completo.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="cf8d8-131">Isso é feito por meio do [Método ResolveTypeLib](resolvetypelib-method.md) que é fornecido pela [interface ITypeLibResolver](itypelibresolver-interface.md), que é passada no parâmetro `pTlbResolver`.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-131">This is accomplished through the [ResolveTypeLib method](resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="cf8d8-132">Quando o caminho completo do arquivo da biblioteca de tipos referenciado é conhecido, a função `LoadTypeLibWithResolver` carrega e adiciona a biblioteca de tipos referenciada à biblioteca de tipos pai, criando uma biblioteca de tipos mestre combinada.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="cf8d8-133">Depois que a função resolve e carrega todas as bibliotecas de tipos referenciadas internamente, ela retorna uma referência à biblioteca de tipos resolvida Master no parâmetro `pptlib`.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="cf8d8-134">A função `LoadTypeLibWithResolver` é geralmente chamada pelo [Tlbexp. exe (tipo exportador da biblioteca de tipos)](../../tools/tlbexp-exe-type-library-exporter.md), que fornece sua própria implementação de [interface ITypeLibResolver](itypelibresolver-interface.md) interna no parâmetro `pTlbResolver`.</span><span class="sxs-lookup"><span data-stu-id="cf8d8-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="cf8d8-135">Se você chamar `LoadTypeLibWithResolver` diretamente, deverá fornecer sua própria implementação de [interface ITypeLibResolver](itypelibresolver-interface.md) .</span><span class="sxs-lookup"><span data-stu-id="cf8d8-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="cf8d8-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="cf8d8-136">Requirements</span></span>  
 <span data-ttu-id="cf8d8-137">**Plataformas:** confira [Requisitos do sistema](../../get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="cf8d8-137">**Platforms:** See [System Requirements](../../get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="cf8d8-138">**Cabeçalho:** TlbRef. h</span><span class="sxs-lookup"><span data-stu-id="cf8d8-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="cf8d8-139">**Biblioteca:** TlbRef. lib</span><span class="sxs-lookup"><span data-stu-id="cf8d8-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="cf8d8-140">**Versão do .NET Framework:** 3,5, 3,0, 2,0</span><span class="sxs-lookup"><span data-stu-id="cf8d8-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="cf8d8-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="cf8d8-141">See also</span></span>

- [<span data-ttu-id="cf8d8-142">Funções auxiliares do Tlbexp</span><span class="sxs-lookup"><span data-stu-id="cf8d8-142">Tlbexp Helper Functions</span></span>](index.md)
- [<span data-ttu-id="cf8d8-143">Função LoadTypeLibEx</span><span class="sxs-lookup"><span data-stu-id="cf8d8-143">LoadTypeLibEx Function</span></span>](https://docs.microsoft.com/previous-versions/windows/desktop/api/oleauto/nf-oleauto-loadtypelibex)
