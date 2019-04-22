---
title: <add> Elemento para <listeners> para <trace>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/trace/listeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <listeners>
- add element for <listeners>
ms.assetid: 81e804a3-ef11-4d39-bbde-bfa012c179e2
ms.openlocfilehash: ba0ffc4f95b9af7fcd319068501ce0bb9714c2ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59089555"
---
# <a name="add-element-for-listeners-for-trace"></a>\<Adicionar > elemento para \<ouvintes > para \<rastreamento >
Adiciona um ouvinte para o **ouvintes** coleção.  
  
 \<configuration>  
\<system.diagnostics>  
\<trace>  
\<listeners>  
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
|**type**|Atributo obrigatório.<br /><br /> Especifica o tipo do ouvinte. Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados em [especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
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
|`listeners`|Especifica um ouvinte que coleta, armazena e encaminha mensagens. Os ouvintes direcionam a saída de rastreamento para um destino apropriado.|  
|`system.diagnostics`|Especifica o elemento raiz para a seção de configuração do ASP.NET.|  
|`trace`|Contém os ouvintes que coletam, armazenam e roteiam mensagens de rastreamento.|  
  
## <a name="remarks"></a>Comentários  
 O <xref:System.Diagnostics.Debug> e <xref:System.Diagnostics.Trace> classes compartilham o mesmo **ouvintes** coleção. Se você adicionar um objeto de ouvinte à coleção em uma dessas classes, a outra classe usa o mesmo ouvinte. As classes de ouvinte derivam o <xref:System.Diagnostics.TraceListener>.  
  
 Se você não especificar o `name` atributo do ouvinte de rastreamento, o <xref:System.Diagnostics.TraceListener.Name%2A> dos padrões de ouvinte de rastreamento para uma cadeia de caracteres vazia (""). Se seu aplicativo tiver somente um ouvinte, você pode adicioná-lo sem especificar um nome e removê-la, especificando uma cadeia de caracteres vazia para o nome. No entanto, se seu aplicativo tiver mais de um ouvinte, você deve especificar nomes exclusivos para cada ouvinte de rastreamento, que permite que você identifique e gerencie os ouvintes de rastreamento individuais dentro de <xref:System.Diagnostics.Debug.Listeners%2A> e <xref:System.Diagnostics.Trace.Listeners%2A> coleções.  
  
> [!NOTE]
>  Adicionando mais de um ouvinte de rastreamento do mesmo tipo e com o mesmo nome resultados no ouvinte de rastreamento somente um desse tipo e nomeie o que está sendo adicionado ao `Listeners` coleção. No entanto, você pode adicionar programaticamente várias escutas idênticas a `Listeners` coleção.  
  
 O valor para o **initializeData** atributo depende do tipo de ouvinte que você cria. Nem todos os ouvintes de rastreamento requerem que você especifique **initializeData**.  
  
> [!NOTE]
>  Quando você usa o `initializeData` atributo, você pode receber o aviso "o atributo 'initializeData' não é declarado" do compilador Este aviso ocorre porque as definições de configuração são validadas em relação a classe base abstrata <xref:System.Diagnostics.TraceListener>, que não reconhece o `initializeData` atributo. Normalmente, você pode ignorar este aviso para as implementações de ouvinte de rastreamento que tem um construtor que aceita um parâmetro.  
  
 A tabela a seguir mostra os ouvintes de rastreamento que são incluídos com o .NET Framework e descreve o valor de suas **initializeData** atributos.  
  
|Classe de ouvintes de rastreamento|valor do atributo initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|O `useErrorStream` de valor para o <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> construtor.  Defina as `initializeData` de atributo para "`true`" para gravar o rastreamento e depuração de saída para <xref:System.Console.Error%2A?displayProperty=nameWithType>; "`false`" para gravar <xref:System.Console.Out%2A?displayProperty=nameWithType>.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|O nome do nome de uma fonte de log de eventos existente.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|O nome do arquivo que o <xref:System.Diagnostics.EventSchemaTraceListener> grava.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|O nome do arquivo que o <xref:System.Diagnostics.TextWriterTraceListener> grava.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|O nome do arquivo que o <xref:System.Diagnostics.XmlWriterTraceListener> grava.|  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar  **\<Adicionar >** elementos para adicionar os ouvintes `MyListener` e `MyEventListener` para o **ouvintes** coleção. `MyListener` cria um arquivo chamado `MyListener.log` e grava a saída para o arquivo. `MyEventListener` cria uma entrada no log de eventos.  
  
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

- <xref:System.Diagnostics.Trace>
- <xref:System.Diagnostics.Debug>
- <xref:System.Diagnostics.EventLogTraceListener>
- <xref:System.Diagnostics.ConsoleTraceListener>
- <xref:System.Diagnostics.TextWriterTraceListener>
- [Esquema de configurações de rastreamento e depuração](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [Ouvintes de rastreamento](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
