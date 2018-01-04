---
title: "Enumeração METAHOST_POLICY_FLAGS"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: reference
api_name: METAHOST_POLICY_FLAGS
api_location: mscoree.dll
api_type: COM
f1_keywords: METAHOST_POLICY_FLAGS
helpviewer_keywords: METAHOST_POLICY_FLAGS enumeration [.NET Framework hosting]
ms.assetid: 3bb4b526-0118-42e2-ba59-c95648528ce9
topic_type: apiref
caps.latest.revision: "21"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 80abed08cc7659d4218dce445be81481bb5a665b
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="metahostpolicyflags-enumeration"></a>Enumeração METAHOST_POLICY_FLAGS
Fornece diretivas de associação que são comuns a maioria dos hosts de tempo de execução. Essa enumeração é usada pelo [Iclrmetahostpolicy](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) método.  
  
## <a name="syntax"></a>Sintaxe  
  
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
  
## <a name="members"></a>Membros  
  
|Membro|Descrição|  
|------------|-----------------|  
|`METAHOST_POLICY_HIGHCOMPAT`|Define a política de alta compatibilidade que não considera qualquer common language runtime (CLR) que é carregado no processo atual. Em vez disso, considera somente os CLRs instalados e as preferências do componente, como derivados do próprio arquivo de assembly, a versão criada em declarado ou o arquivo de configuração.|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|Aplica a política de atualização para o resultado de ligação de versão quando uma correspondência exata não for encontrada, com base no conteúdo do HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades. Isso tem o mesmo efeito que [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|Associação de resultados são retornados como se a imagem fornecida para a chamada iniciada em um novo processo. Atualmente, `GetRequestedRuntime` ignora o conjunto de tempos de execução pode ser carregados e associa com o conjunto de tempo de execução instalado. Esse sinalizador permite que um host determinar quais um EXE associará quando ele é iniciado em tempo de execução.|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|Uma caixa de diálogo de erro será exibida se `GetRequestedRuntime` não consegue encontrar um tempo de execução que é compatível com os parâmetros de entrada. Começando com o [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], essa caixa de diálogo de erro pode assumir a forma de uma caixa de diálogo de recurso do Windows que pergunta se o usuário deseja habilitar o recurso apropriado.|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime`usa a imagem do processo (e qualquer arquivo de configuração correspondente) como entrada adicional para o processo de ligação. Por padrão, `GetRequestedRuntime` não será revertido para o caminho de imagem do processo (normalmente, o arquivo EXE que foi usado para iniciar o processo) ao determinar o tempo de execução para associar a.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime`deve verificar se o SKU apropriado é instalado quando nenhuma informação está disponível no arquivo de configuração. Isso permite que aplicativos que não têm arquivos de configuração falha normalmente em SKUs menores do que a instalação padrão do .NET Framework. Por padrão, `GetRequestedRuntime` não verifica se o SKU apropriado está instalado, a menos que o atributo SKU é especificado no arquivo de configuração `<supportedRuntime />` elemento.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime`deve verificar se o SKU apropriado é instalado quando nenhuma informação está disponível no arquivo de configuração. Isso permite que aplicativos que não têm arquivos de configuração falha normalmente em SKUs menores do que a instalação padrão do .NET Framework. Por padrão, `GetRequestedRuntime` não verifica se o SKU apropriado está instalado, a menos que o atributo SKU é especificado no arquivo de configuração `<supportedRuntime />` elemento.|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime`deve ignorar SEM_FAILCRITICALERRORS (que é definido ao chamar o [SetErrorMode](http://go.microsoft.com/fwlink/p/?LinkId=255242) função) e mostrar a caixa de diálogo de erro. Por padrão, SEM_FAILCRITICALERRORS suprime a caixa de diálogo de erro. Ela foi herdada de outro processo e o erro silencioso pode ser indesejável em seu cenário.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** consulte [requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Metahost.h  
  
 **Biblioteca:** incluído como um recurso no MSCOREE  
  
 **Versões do .NET framework:**[!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também  
 [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)  
 [Método GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
