---
title: Enumeração METAHOST_POLICY_FLAGS
ms.date: 03/30/2017
api_name:
- METAHOST_POLICY_FLAGS
api_location:
- mscoree.dll
api_type:
- COM
f1_keywords:
- METAHOST_POLICY_FLAGS
helpviewer_keywords:
- METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type:
- apiref
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 31ff93b6935c2237a5935c4b40cc30b4129edcd0
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59230597"
---
# <a name="metahostpolicyflags-enumeration"></a><span data-ttu-id="25ffa-102">Enumeração METAHOST_POLICY_FLAGS</span><span class="sxs-lookup"><span data-stu-id="25ffa-102">METAHOST_POLICY_FLAGS Enumeration</span></span>
<span data-ttu-id="25ffa-103">Fornece diretivas de associação que são comuns a maioria dos hosts de tempo de execução.</span><span class="sxs-lookup"><span data-stu-id="25ffa-103">Provides binding policies that are common to most runtime hosts.</span></span> <span data-ttu-id="25ffa-104">Essa enumeração é usada pelo [iclrmetahostpolicy:: Getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) método.</span><span class="sxs-lookup"><span data-stu-id="25ffa-104">This enumeration is used by the [ICLRMetaHostPolicy::GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) method.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="25ffa-105">Sintaxe</span><span class="sxs-lookup"><span data-stu-id="25ffa-105">Syntax</span></span>  
  
```  
typedef enum {  
    METAHOST_POLICY_HIGHCOMPAT              = 0x00,  
    METAHOST_POLICY_APPLY_UPGRADE_POLICY    = 0x08,  
    METAHOST_POLICY_EMULATE_EXE_LAUNCH      = 0x10,  
    METAHOST_POLICY_SHOW_ERROR_DIALOG       = 0x20,  
    METAHOST_POLICY_USE_PROCESS_IMAGE_PATH  = 0x40,  
    METAHOST_POLICY_ENSURE_SKU_SUPPORTED    = 0x80,  
    METAHOST_POLICY_IGNORE_ERROR_MODE       = 0x1000  
  
} METAHOST_POLICY_FLAGS;  
```  
  
## <a name="members"></a><span data-ttu-id="25ffa-106">Membros</span><span class="sxs-lookup"><span data-stu-id="25ffa-106">Members</span></span>  
  
|<span data-ttu-id="25ffa-107">Membro</span><span class="sxs-lookup"><span data-stu-id="25ffa-107">Member</span></span>|<span data-ttu-id="25ffa-108">Descrição</span><span class="sxs-lookup"><span data-stu-id="25ffa-108">Description</span></span>|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|<span data-ttu-id="25ffa-109">Define a política de alta compatibilidade, que não considera qualquer common language runtime (CLR) que é carregado no processo atual.</span><span class="sxs-lookup"><span data-stu-id="25ffa-109">Defines the high-compatibility policy, which does not consider any common language runtime (CLR) that is loaded into the current process.</span></span> <span data-ttu-id="25ffa-110">Em vez disso, ele considera somente os CLRs instalados e as preferências do componente, de conforme derivado do próprio arquivo de assembly, a versão compilado contra declarada ou o arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="25ffa-110">Instead, it considers only the installed CLRs and the preferences of the component, as derived from the assembly file itself, the declared built-against version, or the configuration file.</span></span>|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|<span data-ttu-id="25ffa-111">Aplica a política de atualização para o resultado da associação de versão quando uma correspondência exata não for encontrada, com base no conteúdo da chave HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades.</span><span class="sxs-lookup"><span data-stu-id="25ffa-111">Applies upgrade policy to the version bind result when an exact match is not found, based on the contents of HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\.NETFramework\Policy\Upgrades.</span></span> <span data-ttu-id="25ffa-112">Isso tem o mesmo efeito que [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span><span class="sxs-lookup"><span data-stu-id="25ffa-112">This has the same effect as [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).</span></span>|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|<span data-ttu-id="25ffa-113">Associação de resultados são retornados como se a imagem fornecida para a chamada foram iniciada em um novo processo.</span><span class="sxs-lookup"><span data-stu-id="25ffa-113">Binding results are returned as if the image provided to the call were launched in a new process.</span></span> <span data-ttu-id="25ffa-114">Atualmente, `GetRequestedRuntime` ignora o conjunto de tempos de execução pode ser carregados e a associa com o conjunto de tempo de execução instalado.</span><span class="sxs-lookup"><span data-stu-id="25ffa-114">Currently, `GetRequestedRuntime` ignores the set of loadable runtimes and binds against the set of installed runtimes.</span></span> <span data-ttu-id="25ffa-115">Esse sinalizador permite que um host determinar qual tempo de execução um EXE associará quando ele é iniciado.</span><span class="sxs-lookup"><span data-stu-id="25ffa-115">This flag allows a host to determine which runtime an EXE will bind to when it is launched.</span></span>|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|<span data-ttu-id="25ffa-116">Uma caixa de diálogo de erro será exibida se `GetRequestedRuntime` não consegue encontrar um tempo de execução que é compatível com os parâmetros de entrada.</span><span class="sxs-lookup"><span data-stu-id="25ffa-116">An error dialog box is displayed if `GetRequestedRuntime` is unable to find a runtime that is compatible with the input parameters.</span></span> <span data-ttu-id="25ffa-117">Começando com o [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], essa caixa de diálogo de erro pode assumir a forma de uma caixa de diálogo de recurso do Windows que pergunta se o usuário gostaria de habilitar o recurso apropriado.</span><span class="sxs-lookup"><span data-stu-id="25ffa-117">Beginning with the [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], this error dialog box can take the form of a Windows feature dialog box that asks whether the user would like to enable the appropriate feature.</span></span>|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|<span data-ttu-id="25ffa-118">`GetRequestedRuntime` usa a imagem do processo (e qualquer arquivo de configuração correspondente) como entrada adicional para o processo de associação.</span><span class="sxs-lookup"><span data-stu-id="25ffa-118">`GetRequestedRuntime` uses the process image (and any corresponding configuration file) as additional input to the binding process.</span></span> <span data-ttu-id="25ffa-119">Por padrão, `GetRequestedRuntime` não será revertido para o caminho de imagem do processo (geralmente, o EXE que foi usado para iniciar o processo) ao determinar o tempo de execução para associar a.</span><span class="sxs-lookup"><span data-stu-id="25ffa-119">By default, `GetRequestedRuntime` does not fall back to the process image path (typically, the EXE that was used to launch the process) when determining the runtime to bind to.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="25ffa-120">`GetRequestedRuntime` deve verificar se a SKU adequada é instalada quando nenhuma informação está disponível no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="25ffa-120">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="25ffa-121">Isso permite que os aplicativos que não têm arquivos de configuração normalmente em SKUs menores que a instalação padrão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="25ffa-121">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="25ffa-122">Por padrão, `GetRequestedRuntime` não verifica se o SKU apropriado está instalado, a menos que o atributo SKU é especificado no arquivo de configuração `<supportedRuntime />` elemento.</span><span class="sxs-lookup"><span data-stu-id="25ffa-122">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|<span data-ttu-id="25ffa-123">`GetRequestedRuntime` deve verificar se a SKU adequada é instalada quando nenhuma informação está disponível no arquivo de configuração.</span><span class="sxs-lookup"><span data-stu-id="25ffa-123">`GetRequestedRuntime` must check whether the appropriate SKU is installed when no information is available in the configuration file.</span></span> <span data-ttu-id="25ffa-124">Isso permite que os aplicativos que não têm arquivos de configuração normalmente em SKUs menores que a instalação padrão do .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="25ffa-124">This allows applications that do not have configuration files to fail gracefully on smaller SKUs than the default installation of the .NET Framework.</span></span> <span data-ttu-id="25ffa-125">Por padrão, `GetRequestedRuntime` não verifica se o SKU apropriado está instalado, a menos que o atributo SKU é especificado no arquivo de configuração `<supportedRuntime />` elemento.</span><span class="sxs-lookup"><span data-stu-id="25ffa-125">By default, `GetRequestedRuntime` does not check whether the appropriate SKU is installed unless the SKU attribute is specified in the configuration file `<supportedRuntime />` element.</span></span>|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|<span data-ttu-id="25ffa-126">`GetRequestedRuntime` deve ignorar SEM_FAILCRITICALERRORS (que é definida por meio da chamada a [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) função) e mostrar a caixa de diálogo de erro.</span><span class="sxs-lookup"><span data-stu-id="25ffa-126">`GetRequestedRuntime` should ignore SEM_FAILCRITICALERRORS (which is set by calling the [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) function), and show the error dialog box.</span></span> <span data-ttu-id="25ffa-127">Por padrão, SEM_FAILCRITICALERRORS suprime a caixa de diálogo de erro.</span><span class="sxs-lookup"><span data-stu-id="25ffa-127">By default, SEM_FAILCRITICALERRORS suppresses the error dialog box.</span></span> <span data-ttu-id="25ffa-128">Ela foi herdada de outro processo e o erro silencioso pode ser indesejável em seu cenário.</span><span class="sxs-lookup"><span data-stu-id="25ffa-128">It may have been inherited from another process, and the silent error may be undesirable in your scenario.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="25ffa-129">Comentários</span><span class="sxs-lookup"><span data-stu-id="25ffa-129">Remarks</span></span>  
  
## <a name="requirements"></a><span data-ttu-id="25ffa-130">Requisitos</span><span class="sxs-lookup"><span data-stu-id="25ffa-130">Requirements</span></span>  
 <span data-ttu-id="25ffa-131">**Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).</span><span class="sxs-lookup"><span data-stu-id="25ffa-131">**Platforms:** See [System Requirements](../../../../docs/framework/get-started/system-requirements.md).</span></span>  
  
 <span data-ttu-id="25ffa-132">**Cabeçalho:** Metahost.h</span><span class="sxs-lookup"><span data-stu-id="25ffa-132">**Header:** Metahost.h</span></span>  
  
 <span data-ttu-id="25ffa-133">**Biblioteca:** Incluído como um recurso em mscoree. dll</span><span class="sxs-lookup"><span data-stu-id="25ffa-133">**Library:** Included as a resource in MSCorEE.dll</span></span>  
  
 <span data-ttu-id="25ffa-134">**Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span><span class="sxs-lookup"><span data-stu-id="25ffa-134">**.NET Framework Versions:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="25ffa-135">Consulte também</span><span class="sxs-lookup"><span data-stu-id="25ffa-135">See also</span></span>

- [<span data-ttu-id="25ffa-136">Enumerações de hospedagem</span><span class="sxs-lookup"><span data-stu-id="25ffa-136">Hosting Enumerations</span></span>](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [<span data-ttu-id="25ffa-137">Método GetRequestedRuntime</span><span class="sxs-lookup"><span data-stu-id="25ffa-137">GetRequestedRuntime Method</span></span>](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
