---
title: '&lt;Assert&gt; elemento'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/assert
- http://schemas.microsoft.com/.NetConfiguration/v2.0#assert
helpviewer_keywords:
- <assert> element
- assert element
ms.assetid: ef4c3229-b151-4d85-8091-e6456af9b935
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: ab1644d23e4d6d78b62e701902e5ec39e134b38b
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32745114"
---
# <a name="ltassertgt-element"></a>&lt;Assert&gt; elemento
Especifica se uma caixa de mensagem deve ser exibida ao chamar o método <xref:System.Diagnostics.Debug.Assert%2A?displayProperty=nameWithType>; também especifica o nome do arquivo no qual as mensagens serão gravadas.  
  
 \<configuration>  
\<System. Diagnostics >  
\<Assert >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<assert assertuienabled="true|false" logfilename="file name"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`assertuienabled`|Atributo opcional.<br /><br /> Especifica se exibir uma caixa de mensagem quando o **Assert** método é avaliada como **false**.|  
|`logfilename`|Atributo opcional.<br /><br /> Especifica o nome do arquivo para gravar a mensagem se **Assert** é avaliada como **false**.|  
  
## <a name="assertuienabled-attribute"></a>assertuienabled atributo  
  
|Valor|Descrição|  
|-----------|-----------------|  
|`true`|Exibe a caixa de mensagem. Esse é o padrão.|  
|`false`|Não exibir a caixa de mensagem.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
  
## <a name="remarks"></a>Comentários  
 Ambos os atributos no  **\<assert >** elemento são opcionais. Você pode desabilitar as caixas de mensagem sem especificar um arquivo para gravar as mensagens para, ou você pode especificar um arquivo para gravar mensagens enquanto deixando habilitadas de caixas de mensagem.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como desabilitar Exibindo caixas de mensagem quando você chamar **Assert** e gravar as mensagens de `c:\log.txt`.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <assert assertuienabled="false" logfilename="c:\log.txt"/>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Diagnostics.Debug>  
 [Esquema de configurações de rastreamento e depuração](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
