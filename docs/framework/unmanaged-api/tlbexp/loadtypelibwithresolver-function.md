---
title: "Função LoadTypeLibWithResolver"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
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
caps.latest.revision: 
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f069d09f25575c39db097024384ad1bf14eaaf02
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="loadtypelibwithresolver-function"></a><span data-ttu-id="7d85f-102">Função LoadTypeLibWithResolver</span><span class="sxs-lookup"><span data-stu-id="7d85f-102">LoadTypeLibWithResolver Function</span></span>
<span data-ttu-id="7d85f-103">Carrega uma biblioteca de tipos e usa fornecido [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) para resolver quaisquer bibliotecas de tipo referenciado internamente.</span><span class="sxs-lookup"><span data-stu-id="7d85f-103">Loads a type library and uses the supplied [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) to resolve any internally referenced type libraries.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7d85f-104">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="7d85f-104">Syntax</span></span>  
  
```  
HRESULT LoadTypeLibWithResolver(  
    [in]  LPCOLESTR           szFile,  
    [in]  REGKIND             regkind,  
    [in]  ITypeLibResolver   *pTlbResolver,  
    [out] ITypeLib          **pptlib);  
```  
  
#### <a name="parameters"></a><span data-ttu-id="7d85f-105">Parâmetros</span><span class="sxs-lookup"><span data-stu-id="7d85f-105">Parameters</span></span>  
 `szFile`  
 <span data-ttu-id="7d85f-106">[in] O caminho do arquivo de biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="7d85f-106">[in] The file path of the type library.</span></span>  
  
 `regkind`  
 <span data-ttu-id="7d85f-107">[in] Um [enumeração REGKIND](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx) sinalizador que controla como a biblioteca de tipos é registrada.</span><span class="sxs-lookup"><span data-stu-id="7d85f-107">[in] A [REGKIND enumeration](https://msdn.microsoft.com/library/windows/desktop/ms221159.aspx) flag that controls how the type library is registered.</span></span> <span data-ttu-id="7d85f-108">Os valores possíveis são:</span><span class="sxs-lookup"><span data-stu-id="7d85f-108">Its possible values are:</span></span>  
  
-   <span data-ttu-id="7d85f-109">`REGKIND_DEFAULT`: Use o comportamento de registro padrão.</span><span class="sxs-lookup"><span data-stu-id="7d85f-109">`REGKIND_DEFAULT`: Use default registration behavior.</span></span>  
  
-   <span data-ttu-id="7d85f-110">`REGKIND_REGISTER`: Registre a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="7d85f-110">`REGKIND_REGISTER`: Register this type library.</span></span>  
  
-   <span data-ttu-id="7d85f-111">`REGKIND_NONE`: Não registre a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="7d85f-111">`REGKIND_NONE`: Do not register this type library.</span></span>  
  
 `pTlbResolver`  
 <span data-ttu-id="7d85f-112">[in] Um ponteiro para a implementação de [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span><span class="sxs-lookup"><span data-stu-id="7d85f-112">[in] A pointer to the implementation of the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md).</span></span>  
  
 `pptlib`  
 <span data-ttu-id="7d85f-113">[out] Uma referência à biblioteca de tipos que está sendo carregada.</span><span class="sxs-lookup"><span data-stu-id="7d85f-113">[out] A reference to the type library that is being loaded.</span></span>  
  
## <a name="return-value"></a><span data-ttu-id="7d85f-114">Valor de retorno</span><span class="sxs-lookup"><span data-stu-id="7d85f-114">Return Value</span></span>  
 <span data-ttu-id="7d85f-115">Um dos valores HRESULT listados na tabela a seguir.</span><span class="sxs-lookup"><span data-stu-id="7d85f-115">One of the HRESULT values listed in the following table.</span></span>  
  
|<span data-ttu-id="7d85f-116">Valor retornado</span><span class="sxs-lookup"><span data-stu-id="7d85f-116">Return value</span></span>|<span data-ttu-id="7d85f-117">Significado</span><span class="sxs-lookup"><span data-stu-id="7d85f-117">Meaning</span></span>|  
|------------------|-------------|  
|`S_OK`|<span data-ttu-id="7d85f-118">Êxito.</span><span class="sxs-lookup"><span data-stu-id="7d85f-118">Success.</span></span>|  
|`E_OUTOFMEMORY`|<span data-ttu-id="7d85f-119">Sem memória.</span><span class="sxs-lookup"><span data-stu-id="7d85f-119">Out of memory.</span></span>|  
|`E_POINTER`|<span data-ttu-id="7d85f-120">Um ou mais dos ponteiros são inválidos.</span><span class="sxs-lookup"><span data-stu-id="7d85f-120">One or more of the pointers are invalid.</span></span>|  
|`E_INVALIDARG`|<span data-ttu-id="7d85f-121">Um ou mais argumentos são inválidos.</span><span class="sxs-lookup"><span data-stu-id="7d85f-121">One or more of the arguments are invalid.</span></span>|  
|`TYPE_E_IOERROR`|<span data-ttu-id="7d85f-122">A função não pôde gravar o arquivo.</span><span class="sxs-lookup"><span data-stu-id="7d85f-122">The function could not write to the file.</span></span>|  
|`TYPE_E_REGISTRYACCESS`|<span data-ttu-id="7d85f-123">Não foi possível abrir o banco de dados de registro do sistema.</span><span class="sxs-lookup"><span data-stu-id="7d85f-123">The system registration database could not be opened.</span></span>|  
|`TYPE_E_INVALIDSTATE`|<span data-ttu-id="7d85f-124">Não foi possível abrir a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="7d85f-124">The type library could not be opened.</span></span>|  
|`TYPE_E_CANTLOADLIBRARY`|<span data-ttu-id="7d85f-125">Não foi possível carregar a biblioteca de tipos ou DLL.</span><span class="sxs-lookup"><span data-stu-id="7d85f-125">The type library or DLL could not be loaded.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7d85f-126">Comentários</span><span class="sxs-lookup"><span data-stu-id="7d85f-126">Remarks</span></span>  
 <span data-ttu-id="7d85f-127">O [Tlbexp.exe (exportador da biblioteca)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) chama o `LoadTypeLibWithResolver` função durante o processo de conversão de assembly a biblioteca de tipos.</span><span class="sxs-lookup"><span data-stu-id="7d85f-127">The [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md) calls the `LoadTypeLibWithResolver` function during the assembly-to-type-library conversion process.</span></span>  
  
 <span data-ttu-id="7d85f-128">Essa função carrega a biblioteca com acesso mínimo para registro.</span><span class="sxs-lookup"><span data-stu-id="7d85f-128">This function loads the specified type library with minimal access to the registry.</span></span> <span data-ttu-id="7d85f-129">A função, em seguida, examina a biblioteca de tipos para bibliotecas de tipo referenciado internamente, cada um deles deve ser carregada e adicionada à biblioteca de tipo de pai.</span><span class="sxs-lookup"><span data-stu-id="7d85f-129">The function then examines the type library for internally referenced type libraries, each of which must be loaded and added to the parent type library.</span></span>  
  
 <span data-ttu-id="7d85f-130">Antes de uma biblioteca de tipos referenciada pode ser carregada, seu caminho de arquivo de referência deve ser resolvido para um caminho de arquivo completo.</span><span class="sxs-lookup"><span data-stu-id="7d85f-130">Before a referenced type library can be loaded, its reference file path must be resolved to a full file path.</span></span> <span data-ttu-id="7d85f-131">Isso é feito por meio de [método ResolveTypeLib](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) que é fornecido pelo [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), que é passado no `pTlbResolver` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7d85f-131">This is accomplished through the [ResolveTypeLib method](../../../../docs/framework/unmanaged-api/tlbexp/resolvetypelib-method.md) that is provided by the [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md), which is passed in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="7d85f-132">Quando o caminho completo do arquivo da biblioteca de tipos referenciada é conhecido, o `LoadTypeLibWithResolver` função carrega e adiciona a biblioteca de tipos referenciada na biblioteca de tipo de pai, criando uma biblioteca de tipos mestre combinados.</span><span class="sxs-lookup"><span data-stu-id="7d85f-132">When the full file path of the referenced type library is known, the `LoadTypeLibWithResolver` function loads and adds the referenced type library to the parent type library, creating a combined master type library.</span></span>  
  
 <span data-ttu-id="7d85f-133">Depois que a função resolve e carrega todas as bibliotecas de tipo referenciado internamente, ele retorna uma referência à biblioteca de tipo resolvidos mestre no `pptlib` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7d85f-133">After the function resolves and loads all internally referenced type libraries, it returns a reference to the master resolved type library in the `pptlib` parameter.</span></span>  
  
 <span data-ttu-id="7d85f-134">O `LoadTypeLibWithResolver` função geralmente é chamada pelo [Tlbexp.exe (exportador da biblioteca)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), que fornece seu próprio interno [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementação no `pTlbResolver` parâmetro.</span><span class="sxs-lookup"><span data-stu-id="7d85f-134">The `LoadTypeLibWithResolver` function is generally called by the [Tlbexp.exe (Type Library Exporter)](../../../../docs/framework/tools/tlbexp-exe-type-library-exporter.md), which supplies its own internal [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation in the `pTlbResolver` parameter.</span></span>  
  
 <span data-ttu-id="7d85f-135">Se você chamar `LoadTypeLibWithResolver` diretamente, você deve fornecer seu próprio [interface ITypeLibResolver](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementação.</span><span class="sxs-lookup"><span data-stu-id="7d85f-135">If you call `LoadTypeLibWithResolver` directly, you must supply your own [ITypeLibResolver interface](../../../../docs/framework/unmanaged-api/tlbexp/itypelibresolver-interface.md) implementation.</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="7d85f-136">Requisitos</span><span class="sxs-lookup"><span data-stu-id="7d85f-136">Requirements</span></span>  
 <span data-ttu-id="7d85f-137">**Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="7d85f-137">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="7d85f-138">**Cabeçalho:** TlbRef.h</span><span class="sxs-lookup"><span data-stu-id="7d85f-138">**Header:** TlbRef.h</span></span>  
  
 <span data-ttu-id="7d85f-139">**Biblioteca:** TlbRef.lib</span><span class="sxs-lookup"><span data-stu-id="7d85f-139">**Library:** TlbRef.lib</span></span>  
  
 <span data-ttu-id="7d85f-140">**Versão do .NET framework:** 2.0, 3.0, 3.5</span><span class="sxs-lookup"><span data-stu-id="7d85f-140">**.NET Framework Version:** 3.5, 3.0, 2.0</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7d85f-141">Consulte também</span><span class="sxs-lookup"><span data-stu-id="7d85f-141">See Also</span></span>  
 [<span data-ttu-id="7d85f-142">Funções auxiliares do Tlbexp</span><span class="sxs-lookup"><span data-stu-id="7d85f-142">Tlbexp Helper Functions</span></span>](../../../../docs/framework/unmanaged-api/tlbexp/index.md)  
 <span data-ttu-id="7d85f-143">[Função LoadTypeLibEx](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)</span><span class="sxs-lookup"><span data-stu-id="7d85f-143">[LoadTypeLibEx Function](https://msdn.microsoft.com/library/windows/desktop/ms221249\(v=vs.85\).aspx)</span></span>
