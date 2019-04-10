---
title: Elemento <NetFx40_PInvokeStackResilience>
ms.date: 03/30/2017
helpviewer_keywords:
- <NetFx40_PInvokeStackResilience> element
- NetFx40_PInvokeStackResilience element
ms.assetid: 39fb1588-72a4-4479-af74-0605233b68bd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 725bd715f6e70dff08929e58d588a3d8561d5011
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/08/2019
ms.locfileid: "59224228"
---
# <a name="netfx40pinvokestackresilience-element"></a>\<NetFx40_PInvokeStackResilience > elemento
Especifica se o tempo de execução corrige automaticamente declarações de invocação de plataforma incorretas em tempo de execução, às custas de transições mais lentas entre o código gerenciado e não gerenciado.  
  
 \<configuration>  
\<runtime>  
<NetFx40_PInvokeStackResilience>  
  
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
|`0`|O tempo de execução usa a arquitetura introduzida de marshaling de interoperabilidade mais rápida a [!INCLUDE[net_v40_long](../../../../../includes/net-v40-long-md.md)], que não o detecta e declarações de invocação de plataforma incorreta de correção. Esse é o padrão.|  
|`1`|Declarações de invocação de tempo de execução usa mais lentas transições que detectam e corrigir a plataforma incorreta.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre opções de inicialização do tempo de execução.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento permite que você troque o marshaling de interoperabilidade mais rápido para declarações de invocação de resiliência de tempo de execução na plataforma incorreta.  
  
 Começando com o [!INCLUDE[net_v40_short](../../../../../includes/net-v40-short-md.md)], uma arquitetura de marshaling de interoperabilidade simplificada fornece uma melhoria significativa de desempenho para transições do código gerenciado para código não gerenciado. Em versões anteriores do .NET Framework, a plataforma incorreta de camada detectada marshaling declarações em plataformas de 32 bits de invocação e corrigidas automaticamente a pilha. A nova arquitetura de marshaling elimina essa etapa. Como resultado, as transições são muito rápidas, mas a declaração de invocação de uma plataforma incorreta pode causar uma falha no programa.  
  
 Para que seja fácil detectar declarações incorretas durante o desenvolvimento, a experiência de depuração do Visual Studio foi aprimorado. O [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md) Assistente para depuração gerenciada (MDA) notifica você da plataforma incorreta de declarações de invocação quando seu aplicativo está em execução com o depurador anexado.  
  
 Para lidar com cenários em que o seu aplicativo usa os componentes que você não pode recompilar e que têm invocação de plataforma incorretas declarações, você pode usar o `NetFx40_PInvokeStackResilience` elemento. Adição deste elemento ao arquivo de configuração de aplicativo com `enabled="1"` aceitar um modo de compatibilidade com o comportamento de versões anteriores do .NET Framework, às custas de transições mais lentas. Assemblies que foram compilados em relação a versões anteriores do .NET Framework são aceitos automaticamente esse modo de compatibilidade e não é necessário para esse elemento.  
  
## <a name="configuration-file"></a>Arquivo de Configuração  
 Esse elemento pode ser usado apenas no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 A exemplo a seguir mostra como as declarações para um aplicativo, às custas de transições mais lentas entre de invocação de plataforma para aceitar o aumento da resiliência contra incorreto gerenciado e código não gerenciado.  
  
```xml  
<configuration>  
   <runtime>  
      <NetFx40_PInvokeStackResilience enabled="1"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também

- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [pInvokeStackImbalance](../../../../../docs/framework/debug-trace-profile/pinvokestackimbalance-mda.md)
