---
title: '&lt;NetFx40_PInvokeStackResilience&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
caps.latest.revision: "8"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.openlocfilehash: 3e77e43ed9d7520cbbcf453d067a49de3a86de3f
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltnetfx40pinvokestackresiliencegt-element"></a>&lt;NetFx40_PInvokeStackResilience&gt; elemento
Especifica se o tempo de execução corrige automaticamente declarações de invocação de plataforma incorretas em tempo de execução, às custas de transições mais lentas entre o código gerenciado e não gerenciado.  
  
 \<configuration>  
\<tempo de execução >  
< NetFx40_PInvokeStackResilience >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<NetFx40_PInvokeStackResilience  enabled="1|0"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o tempo de execução detecta plataforma incorreta declarações de invocação e corrige automaticamente a pilha em tempo de execução em plataformas de 32 bits.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`0`|O tempo de execução usa o mais rápido interop marshaling arquitetura introduzida no [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], que não detecta e declarações de invocação de plataforma incorreta de correção. Esse é o padrão.|  
|`1`|Declarações de invocação de tempo de execução usa mais lentas transições que detectam e corrigir plataforma incorreta.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento permite trocar o marshaling de interoperabilidade mais rápido para resiliência de tempo de execução na plataforma incorreta de invocação de declarações.  
  
 Começando com o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], um simplificada interop marshaling arquitetura fornece uma melhoria significativa de desempenho para transições do código gerenciado para código não gerenciado. Em versões anteriores do .NET Framework, a plataforma incorreta de camada detectada marshaling invocar declarações em plataformas de 32 bits e corrigidas automaticamente a pilha. A nova arquitetura de marshaling elimina essa etapa. Como resultado, as transições são muito rápidas, mas a declaração de invocação de uma plataforma incorreta pode causar uma falha de programa.  
  
 Para facilitar a detectar declarações incorretas durante o desenvolvimento, a experiência de depuração do Visual Studio foi aprimorado. O [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) Assistente de depuração gerenciado (MDA) notifica você plataforma incorreta invoca declarações quando seu aplicativo está em execução com o depurador anexado.  
  
 Para lidar com cenários em que o seu aplicativo usa os componentes que não é possível recompilar e que têm incorretova invocação de plataforma declarações, você pode usar o `NetFx40_PInvokeStackResilience` elemento. Adicionar esse elemento para o arquivo de configuração de aplicativo com `enabled="1"` aceita em um modo de compatibilidade com o comportamento de versões anteriores do .NET Framework, às custas de transições mais lentas. Assemblies que foram compilados em versões anteriores do .NET Framework são aceitos automaticamente para este modo de compatibilidade e não é necessário para este elemento.  
  
## <a name="configuration-file"></a>Arquivo de Configuração  
 Esse elemento pode ser usado apenas no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra como declarações para um aplicativo, às custas de mais lentos transições entre uma invocação de plataforma para optar pelo maior resiliência contra incorreto gerenciado e código não gerenciado.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
