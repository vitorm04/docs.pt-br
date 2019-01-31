---
title: Elemento <gcConcurrent>
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
ms.openlocfilehash: ae20e33f610acf77f2039b94803a19d371b771c0
ms.sourcegitcommit: 14355b4b2fe5bcf874cac96d0a9e6376b567e4c7
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/30/2019
ms.locfileid: "55265981"
---
# <a name="gcconcurrent-element"></a>\<gcConcurrent > elemento
Especifica se o common language runtime executa a coleta de lixo em um thread separado.  
  
 \<configuration>  
\<runtime>  
\<gcConcurrent>  
  
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
|`false`|Não executa a coleta de lixo simultaneamente.|  
|`true`|Executa a coleta de lixo simultaneamente. Esse é o padrão.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`runtime`|Contém informações sobre associação do assembly e coleta de lixo.|  
  
## <a name="remarks"></a>Comentários  
 Antes do .NET Framework 4, coleta de lixo de estação de trabalho com suporte a coleta de lixo simultânea, o que é executada a coleta de lixo em segundo plano em um thread separado. No .NET Framework 4, a coleta de lixo simultânea foi substituída pelo GC, que também executa a coleta de lixo em segundo plano em um thread separado em segundo plano. Começando com o .NET Framework 4.5, a coleta em segundo plano foram disponibilizada na coleta de lixo do servidor. O `<gcConcurrent>` elemento controla se o tempo de execução executa qualquer simultânea ou em segundo plano coleta de lixo, se ele estiver disponível, ou se ele executa a coleta de lixo em primeiro plano.  
  
> [!WARNING]
>  Começando com o .NET Framework 4, a coleta de lixo simultânea é substituída pela coleta de lixo em segundo plano. Os termos *simultâneas* e *plano de fundo* são usados alternadamente na documentação do .NET Framework. Para desabilitar a coleta de lixo em segundo plano, use o `<gcConcurrent>` elemento, conforme discutido neste artigo.  
  
 Por padrão, o tempo de execução usa simultâneos ou a coleta de lixo em segundo plano, que é otimizado para latência. Se seu aplicativo envolve a interação do usuário pesado, deixe a coleta de lixo simultânea habilitada para minimizar o tempo de pausa do aplicativo para executar a coleta de lixo. Se você definir a `enabled` atributo o `<gcConcurrent>` elemento a ser `false`, o tempo de execução usa a coleta de lixo não simultânea, que é otimizada para taxa de transferência. O arquivo de configuração a seguir desabilita a coleta de lixo em segundo plano.  
  
```xml  
<configuration>  
   <runtime>  
      <gcConcurrent enabled="false"/>  
   </runtime>  
</configuration>  
```  
  
 Se não houver um `<gcConcurrentSetting>` configuração no arquivo de configuração do computador, ele define o valor padrão para todos os aplicativos do .NET Framework. O arquivo de configuração de máquina substitui o arquivo de configuração de aplicativo.  
  
 Para obter mais informações sobre simultâneas e coleta de lixo em segundo plano, consulte a seção "coleta de lixo simultânea" a [conceitos básicos da coleta de lixo](../../../../../docs/standard/garbage-collection/fundamentals.md) tópico.  
  
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
- [Esquema de configurações do tempo de execução](../../../../../docs/framework/configure-apps/file-schema/runtime/index.md)
- [Esquema de arquivos de configuração](../../../../../docs/framework/configure-apps/file-schema/index.md)
- [Conceitos básicos da coleta de lixo](../../../../../docs/standard/garbage-collection/fundamentals.md)
