---
title: <add>Elemento <listeners> para para<trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: c64673908dc9afe67d97c08f93e5b9d9533bd34d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153666"
---
# <a name="add-element-for-listeners-for-trace"></a>\<adicionar> \<Element para \<os ouvintes> para rastrear>
Adiciona um ouvinte à coleção **de ouvintes.**  

[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<traçar>**](trace-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ouvintes>**](listeners-element-for-trace.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<adicionar>**

## <a name="syntax"></a>Sintaxe  
  
```xml  
<add name="name"
     type="trace listener class name, Version, Culture, PublicKeyToken"  
     initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**type**|Atributo obrigatório.<br /><br /> Especifica o tipo do ouvinte. Você deve usar uma string que atenda aos requisitos especificados na [Especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**Initializedata**|Atributo opcional.<br /><br /> A seqüência passou para o construtor para a classe especificada.|  
|**name**|Atributo opcional.<br /><br /> Especifica o nome do ouvinte.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de filtro](filter-element-for-add-for-listeners-for-trace.md)|Adiciona um filtro a um `Listeners` ouvinte na coleção para um rastreamento.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`listeners`|Especifica um ouvinte que coleta, armazena e encaminha mensagens. Os ouvintes direcionam a saída de rastreamento para um alvo apropriado.|  
|`system.diagnostics`|Especifica o elemento raiz para a seção de configuração ASP.NET.|  
|`trace`|Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.|  
  
## <a name="remarks"></a>Comentários  
 As <xref:System.Diagnostics.Debug> <xref:System.Diagnostics.Trace> aulas compartilham a mesma coleção **de Ouvintes.** Se você adicionar um objeto de ouvinte à coleção em uma dessas classes, a outra classe usará o mesmo ouvinte. As classes de ouvintes derivam do <xref:System.Diagnostics.TraceListener>.  
  
 Se você não `name` especificar o atributo <xref:System.Diagnostics.TraceListener.Name%2A> do ouvinte de rastreamento, o do ouvinte de rastreamento será padrão para uma seqüência de string vazia (""). Se o aplicativo tiver apenas um ouvinte, você pode adicioná-lo sem especificar um nome e removê-lo especificando uma seqüência vazia para o nome. No entanto, se o seu aplicativo tiver mais de um ouvinte, você deve especificar nomes únicos <xref:System.Diagnostics.Debug.Listeners%2A> <xref:System.Diagnostics.Trace.Listeners%2A> para cada ouvinte de rastreamento, o que permite identificar e gerenciar ouvintes de rastreamento individual dentro das coleções e coleções.  
  
> [!NOTE]
> Adicionar mais de um ouvinte de rastreamento do mesmo tipo e com o mesmo nome resulta `Listeners` em apenas um ouvinte de rastreamento desse tipo e nome sendo adicionado à coleção. No entanto, você pode adicionar programáticamente vários ouvintes idênticos à `Listeners` coleção.  
  
 O valor para o atributo **inicializeData** depende do tipo de ouvinte que você cria. Nem todos os ouvintes de rastreamento exigem que você especifique **inicializarData**.  
  
> [!NOTE]
> Quando você `initializeData` usa o atributo, você pode obter o aviso do compilador "O atributo 'initializeData' não é declarado." Esse aviso ocorre porque as configurações são <xref:System.Diagnostics.TraceListener>validadas em `initializeData` relação à classe base abstrata, que não reconhece o atributo. Normalmente, você pode ignorar este aviso para implementações de ouvintes de rastreamento que tenham um construtor que leva um parâmetro.  
  
 A tabela a seguir mostra os ouvintes de rastreamento que estão incluídos no .NET Framework e descreve o valor de seus atributos **inicializeData.**  
  
|Classe de ouvinte de rastreamento|inicializarvalor do atributoData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|O `useErrorStream` valor <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> para o construtor.  Defina `initializeData` o`true`atributo como " " <xref:System.Console.Error%2A?displayProperty=nameWithType>para escrever a saída de traço e depuração para ; "Para`false`escrever. <xref:System.Console.Out%2A?displayProperty=nameWithType>|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|O nome do nome de uma fonte de registro de eventos existente.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|O nome do arquivo <xref:System.Diagnostics.EventSchemaTraceListener> para o que ele escreve.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|O nome do arquivo <xref:System.Diagnostics.TextWriterTraceListener> para o que ele escreve.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|O nome do arquivo <xref:System.Diagnostics.XmlWriterTraceListener> para o que ele escreve.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar `MyListener` `MyEventListener` ** \<adicionar elementos>** para adicionar os ouvintes e a coleção **Ouvintes.** `MyListener`cria um `MyListener.log` arquivo chamado e grava a saída para o arquivo. `MyEventListener`cria uma entrada no registro de eventos.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <trace autoflush="true" indentsize="0">  
         <listeners>  
            <add name="myListener" type="System.Diagnostics.TextWriterTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089" initializeData="c:\myListener.log" />  
            <add name="MyEventListener"  
                 type="System.Diagnostics.EventLogTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"                 initializeData="MyConfigEventLog"/>  
            <add name="configConsoleListener"  
                 type="System.Diagnostics.ConsoleTraceListener, system, version=1.0.3300.0, Culture=neutral, PublicKeyToken=b77a5c561934e089"/>  
         </listeners>  
      </trace>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [Esquema de configurações de rastreamento e depuração](index.md)
- [Ouvintes de rastreamento](../../../debug-trace-profile/trace-listeners.md)
