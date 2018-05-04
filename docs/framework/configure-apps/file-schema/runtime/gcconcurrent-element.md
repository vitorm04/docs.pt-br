---
title: '&lt;gcConcurrent&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/runtime/gcConcurrent
- http://schemas.microsoft.com/.NetConfiguration/v2.0#gcConcurrent
helpviewer_keywords:
- container tags, <gcConcurrent> element
- gcConcurrent element
- <gcConcurrent> element
ms.assetid: 503f55ba-26ed-45ac-a2ea-caf994da04cd
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: ee00c3a307523d2cae831274630ad6828cd9daf6
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltgcconcurrentgt-element"></a>&lt;gcConcurrent&gt; elemento
Especifica se o common language runtime executa a coleta de lixo em um thread separado.  
  
 \<configuration>  
\<runtime>  
\<gcConcurrent >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<gcConcurrent    
   enabled="true|false"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`enabled`|Atributo obrigatório.<br /><br /> Especifica se o tempo de execução executa a coleta de lixo simultaneamente.|  
  
## <a name="enabled-attribute"></a>Atributo habilitado  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`false`|Não executar coleta de lixo simultaneamente.|  
|`true`|Executa a coleta de lixo simultaneamente. Esse é o padrão.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Antes do .NET Framework 4, coleta de lixo da estação de trabalho com suporte a coleta de lixo simultânea, que é executada a coleta de lixo em segundo plano em um thread separado. No .NET Framework 4, coleta de lixo simultânea foi substituída pelo plano de fundo GC, que também executa a coleta de lixo em segundo plano em um thread separado. Começando com o .NET Framework 4.5, coleção de plano de fundo se tornaram disponível na coleta de lixo do servidor. O `<gcConcurrent>` elemento controla se o tempo de execução executa qualquer simultâneas ou plano de fundo coleta de lixo, se ele estiver disponível, ou se ele executa a coleta de lixo em primeiro plano.  
  
> [!WARNING]
>  Começando com o .NET Framework 4, coleta de lixo simultânea é substituída pela coleta de lixo em segundo plano. Os termos de *simultâneos* e *em segundo plano* são intercambiáveis na documentação do .NET Framework. Para desabilitar a coleta de lixo em segundo plano, use o `<gcConcurrent>` elemento, conforme discutido neste artigo.  
  
 Por padrão, o tempo de execução usa simultâneas ou coleta de lixo em segundo plano, que é otimizado para latência. Se seu aplicativo envolve a interação do usuário pesado, deixe a coleta de lixo simultânea habilitada para minimizar o tempo de pausa do aplicativo para executar a coleta de lixo. Se você definir o `enabled` atributo do `<gcConcurrent>` elemento `false`, o tempo de execução usa a coleta de lixo não simultânea, que é otimizada para taxa de transferência. O arquivo de configuração a seguir desabilita a coleta de lixo em segundo plano.  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 Se houver um `<gcConcurrentSetting>` configuração no arquivo de configuração de máquina, ele define o valor padrão para todos os aplicativos do .NET Framework. O parâmetro de arquivo de configuração de máquina substitui a configuração de arquivo de configuração do aplicativo.  
  
 Para obter mais informações sobre simultâneas e coleta de lixo em segundo plano, consulte a seção "coleta de lixo simultânea" o [conceitos básicos de coleta de lixo](../../../../../docs/standard/garbage-collection/fundamentals.md) tópico.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir habilita a coleta de lixo simultânea.  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="true"/>  
   </runtime>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)  
 [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)  
 [Conceitos básicos da coleta de lixo](../../../../../docs/standard/garbage-collection/fundamentals.md)
