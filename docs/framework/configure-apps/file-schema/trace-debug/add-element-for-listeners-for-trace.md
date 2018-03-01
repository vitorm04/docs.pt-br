---
title: '&lt;Adicionar&gt; elemento para &lt;ouvintes&gt; para &lt;rastreamento&gt;'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: eb624052c3638cb49abe143ebd4173a5ee85a054
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltlistenersgt-for-lttracegt"></a>&lt;Adicionar&gt; elemento para &lt;ouvintes&gt; para &lt;rastreamento&gt;
Adiciona um ouvinte para o **ouvintes** coleção.  
  
 \<configuration>  
\<System. Diagnostics >  
\<rastreamento >  
\<ouvintes >  
\<add>  
  
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
|**type**|Atributo obrigatório.<br /><br /> Especifica o tipo de ouvinte. Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados em [especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|**initializeData**|Atributo opcional.<br /><br /> A cadeia de caracteres passada para o construtor para a classe especificada.|  
|**name**|Atributo opcional.<br /><br /> Especifica o nome do ouvinte.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-trace.md)|Adiciona um filtro a um ouvinte no `Listeners` coleção para um rastreamento.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`listeners`|Especifica um ouvinte que coleta, armazena e roteamento de mensagens. Os ouvintes direcionam a saída de rastreamento para um destino satisfatório.|  
|`system.diagnostics`|Especifica o elemento raiz para a seção de configuração do ASP.NET.|  
|`trace`|Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.|  
  
## <a name="remarks"></a>Comentários  
 O <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace> classes compartilham o mesmo **ouvintes** coleção. Se você adicionar um objeto de ouvinte para a coleção em uma dessas classes, de outra classe usa o mesmo ouvinte. As classes de ouvinte derivam de <xref:System.Diagnostics.TraceListener>.  
  
 Se você não especificar o `name` atributo do ouvinte de rastreamento, o <xref:System.Diagnostics.TraceListener.Name%2A> os padrões de ouvinte de rastreamento para uma cadeia de caracteres vazia (""). Se seu aplicativo tiver somente um ouvinte, você pode adicioná-lo sem especificar um nome e removê-la, especificando uma cadeia de caracteres vazia para o nome. No entanto, se seu aplicativo tiver mais de um ouvinte, você deve especificar nomes exclusivos para cada ouvinte de rastreamento, que permite identificar e gerenciar os ouvintes de rastreamento individuais dentro de <xref:System.Diagnostics.Debug.Listeners%2A> e <xref:System.Diagnostics.Trace.Listeners%2A> coleções.  
  
> [!NOTE]
>  Adicionar mais de um ouvinte de rastreamento do mesmo tipo e com o mesmo nome resultados no ouvinte de rastreamento somente uma desse tipo e nome que está sendo adicionado para o `Listeners` coleção. No entanto, você pode adicionar vários ouvintes idênticos para programaticamente o `Listeners` coleção.  
  
 O valor para o **initializeData** atributo depende do tipo de ouvinte que você criar. Nem todos os ouvintes de rastreamento requerem que você especifique **initializeData**.  
  
> [!NOTE]
>  Quando você usa o `initializeData` atributo, você pode obter o compilador aviso "o atributo 'initializeData' não é declarado". Este aviso ocorre porque as definições de configuração são validadas em relação a classe base abstrata <xref:System.Diagnostics.TraceListener>, que não reconhece o `initializeData` atributo. Normalmente, você pode ignorar este aviso para implementações de ouvinte de rastreamento que tem um construtor que usa um parâmetro.  
  
 A tabela a seguir mostra os ouvintes de rastreamento que são incluídos com o .NET Framework e descreve o valor de suas **initializeData** atributos.  
  
|Classe de ouvinte de rastreamento|valor do atributo initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|O `useErrorStream` valor para o <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> construtor.  Definir o `initializeData` atributo "`true`" para gravar o rastreamento e depuração de saída para <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" para gravar <xref:System.Console.Out%2A?displayProperty=nameWithType>.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|O nome do nome de uma fonte de log de eventos existente.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|O nome do arquivo que o <xref:System.Diagnostics.EventSchemaTraceListener> grava.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|O nome do arquivo que o <xref:System.Diagnostics.TextWriterTraceListener> grava.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|O nome do arquivo que o <xref:System.Diagnostics.XmlWriterTraceListener> grava.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar  **\<Adicionar >** elementos para adicionar os ouvintes `MyListener` e `MyEventListener` para o **ouvintes** coleção. `MyListener`cria um arquivo chamado `MyListener.log` e grava a saída para o arquivo. `MyEventListener`cria uma entrada no log de eventos.  
  
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
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Diagnostics.Trace>  
 <xref:System.Diagnostics.Debug>  
 <xref:System.Diagnostics.EventLogTraceListener>  
 <xref:System.Diagnostics.ConsoleTraceListener>  
 <xref:System.Diagnostics.TextWriterTraceListener>  
 [Esquema de configurações de rastreamento e depuração](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [Ouvintes de rastreamento](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
