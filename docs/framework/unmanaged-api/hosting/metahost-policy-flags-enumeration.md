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
ms.openlocfilehash: 37a6dc0caa81a365727bfc32a6a0363bb7e1713d
ms.sourcegitcommit: ffd7dd79468a81bbb0d6449f6d65513e050c04c4
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/21/2019
ms.locfileid: "65960148"
---
# <a name="metahostpolicyflags-enumeration"></a>Enumeração METAHOST_POLICY_FLAGS
Fornece diretivas de associação que são comuns a maioria dos hosts de tempo de execução. Essa enumeração é usada pelo [iclrmetahostpolicy:: Getrequestedruntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md) método.  
  
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
|`METAHOST_POLICY_HIGHCOMPAT`|Define a política de alta compatibilidade, que não considera qualquer common language runtime (CLR) que é carregado no processo atual. Em vez disso, ele considera somente os CLRs instalados e as preferências do componente, de conforme derivado do próprio arquivo de assembly, a versão compilado contra declarada ou o arquivo de configuração.|  
|`METAHOST_POLICY_APPLY_UPGRADE_POLICY`|Aplica a política de atualização para o resultado da associação de versão quando uma correspondência exata não for encontrada, com base no conteúdo da chave HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\\. NETFramework\Policy\Upgrades. Isso tem o mesmo efeito que [RUNTIME_INFO_UPGRADE_VERSION](../../../../docs/framework/unmanaged-api/hosting/runtime-info-flags-enumeration.md).|  
|`METAHOST_POLICY_EMULATE_EXE_LAUNCH`|Associação de resultados são retornados como se a imagem fornecida para a chamada foram iniciada em um novo processo. Atualmente, `GetRequestedRuntime` ignora o conjunto de tempos de execução pode ser carregados e a associa com o conjunto de tempo de execução instalado. Esse sinalizador permite que um host determinar qual tempo de execução um EXE associará quando ele é iniciado.|  
|`METAHOST_POLICY_SHOW_ERROR_DIALOG`|Uma caixa de diálogo de erro será exibida se `GetRequestedRuntime` não consegue encontrar um tempo de execução que é compatível com os parâmetros de entrada. Começando com o [!INCLUDE[net_v45](../../../../includes/net-v45-md.md)], essa caixa de diálogo de erro pode assumir a forma de uma caixa de diálogo de recurso do Windows que pergunta se o usuário gostaria de habilitar o recurso apropriado.|  
|`METAHOST_POLICY_USE_PROCESS_IMAGE_PATH`|`GetRequestedRuntime` usa a imagem do processo (e qualquer arquivo de configuração correspondente) como entrada adicional para o processo de associação. Por padrão, `GetRequestedRuntime` não será revertido para o caminho de imagem do processo (geralmente, o EXE que foi usado para iniciar o processo) ao determinar o tempo de execução para associar a.|  
|`METAHOST_POLICY_ENSURE_SKU_SUPPORTED`|`GetRequestedRuntime` deve verificar se a SKU adequada é instalada quando nenhuma informação está disponível no arquivo de configuração. Isso permite que os aplicativos que não têm arquivos de configuração normalmente em SKUs menores que a instalação padrão do .NET Framework. Por padrão, `GetRequestedRuntime` não verifica se o SKU apropriado está instalado, a menos que o atributo SKU é especificado no arquivo de configuração `<supportedRuntime />` elemento.|  
|`METAHOST_POLICY_IGNORE_ERROR_MODE`|`GetRequestedRuntime` deve ignorar SEM_FAILCRITICALERRORS (que é definida por meio da chamada a [SetErrorMode](https://go.microsoft.com/fwlink/p/?LinkId=255242) função) e mostrar a caixa de diálogo de erro. Por padrão, SEM_FAILCRITICALERRORS suprime a caixa de diálogo de erro. Ela foi herdada de outro processo e o erro silencioso pode ser indesejável em seu cenário.|  
  
## <a name="remarks"></a>Comentários  
  
## <a name="requirements"></a>Requisitos  
 **Plataformas:** Confira [Requisitos de sistema](../../../../docs/framework/get-started/system-requirements.md).  
  
 **Cabeçalho:** Metahost.h  
  
 **Biblioteca:** Incluído como um recurso em mscoree. dll  
  
 **Versões do .NET Framework:** [!INCLUDE[net_current_v40plus](../../../../includes/net-current-v40plus-md.md)]  
  
## <a name="see-also"></a>Consulte também

- [Enumerações de hospedagem](../../../../docs/framework/unmanaged-api/hosting/hosting-enumerations.md)
- [Método GetRequestedRuntime](../../../../docs/framework/unmanaged-api/hosting/iclrmetahostpolicy-getrequestedruntime-method.md)
