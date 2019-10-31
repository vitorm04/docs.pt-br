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
ms.openlocfilehash: a028d2a8116de4df79f662ee8b2768e6e070428a
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/30/2019
ms.locfileid: "73141390"
---
# <a name="metahost_policy_flags-enumeration"></a>Enumeração METAHOST_POLICY_FLAGS
Fornece políticas de associação que são comuns à maioria dos hosts de tempo de execução. Essa enumeração é usada pelo método [ICLRMetaHostPolicy:: GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) .  
  
## <a name="syntax"></a>Sintaxe  
  
```cpp  
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
|`METAHOST_POLICY_HIGHCOMPAT`|Define a política de alta compatibilidade, que não considera Common Language Runtime (CLR) que é carregado no processo atual. Em vez disso, ele considera apenas o CLRs instalado e as preferências do componente, como derivado do próprio arquivo de assembly, a versão interna declarada ou o arquivo de configuração.|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|Aplica a política de atualização ao resultado da Associação de versão quando uma correspondência exata não é encontrada, com base no conteúdo de HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades. Isso tem o mesmo efeito que [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|Os resultados da associação são retornados como se a imagem fornecida à chamada fosse iniciada em um novo processo. Atualmente, `GetRequestedRuntime` ignora o conjunto de tempos de execução carregável e é associado ao conjunto de tempos de execução instalados. Esse sinalizador permite que um host determine a qual tempo de execução um EXE se associará quando for iniciado.|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|Uma caixa de diálogo de erro será exibida se `GetRequestedRuntime` não conseguir encontrar um tempo de execução compatível com os parâmetros de entrada. A partir do .NET Framework 4,5, essa caixa de diálogo de erro pode assumir a forma de uma caixa de diálogo de recurso do Windows que pergunta se o usuário deseja habilitar o recurso apropriado.|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime` usa a imagem do processo (e qualquer arquivo de configuração correspondente) como entrada adicional para o processo de associação. Por padrão, o `GetRequestedRuntime` não volta para o caminho da imagem do processo (normalmente, o EXE que foi usado para iniciar o processo) ao determinar o tempo de execução ao qual se associar.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime` deve verificar se o SKU apropriado está instalado quando não há informações disponíveis no arquivo de configuração. Isso permite que aplicativos que não têm arquivos de configuração falhem normalmente em SKUs menores do que a instalação padrão do .NET Framework. Por padrão, `GetRequestedRuntime` não verifica se o SKU apropriado está instalado, a menos que o atributo SKU seja especificado no elemento de `<supportedRuntime />` do arquivo de configuração.|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime` deve ignorar SEM_FAILCRITICALERRORS (que é definido chamando a função [SetError](https://go.microsoft.com/fwlink/p/?LinkId=255242) ) e mostrar a caixa de diálogo de erro. Por padrão, SEM_FAILCRITICALERRORS suprime a caixa de diálogo de erro. Ele pode ter sido herdado de outro processo e o erro silencioso pode ser indesejável em seu cenário.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** confira [Requisitos do sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** MetaHost. h  
  
 **Biblioteca:** Incluído como um recurso em MSCorEE. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [Método GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
