---
title: <add> Elemento para <listeners> para <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 4d2952e29b09fcf9f81624317e30caf301a61a51
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61701483"
---
# <a name="add-element-for-listeners-for-source"></a>\<Adicionar > elemento para \<ouvintes > para \<origem >
Adiciona um ouvinte na coleção `Listeners` de uma origem de rastreamento.  
  
 \<configuration>  
\<system.diagnostics>  
\<sources>  
\<origem >  
\<listeners>  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<add name="name"   
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`type`|Com atributo obrigatório, a menos que você está fazendo referência a um ouvinte na `sharedListeners` coleção na qual caso, você só precisa fazer referência a ele por nome (consulte a [exemplo](#example)).<br /><br /> Especifica o tipo do ouvinte. Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados em [especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atributo opcional.<br /><br /> A cadeia de caracteres passada para o construtor para a classe especificada. Um <xref:System.Configuration.ConfigurationException> será gerada se a classe não tem um construtor que aceita uma cadeia de caracteres.|  
|`name`|Atributo opcional.<br /><br /> Especifica o nome do ouvinte.|  
|`traceOutputOptions`|Atributo opcional.<br /><br /> Especifica o <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> valor da propriedade para o ouvinte de rastreamento.|  
|[atributos personalizados]|Atributos opcionais.<br /><br /> Especifica o valor para os atributos de ouvinte específico identificado pelo <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> método para esse ouvinte. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> é um exemplo de um atributo extra exclusivo para o <xref:System.Diagnostics.DelimitedListTraceListener> classe.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-listeners-for-source.md)|Adiciona um filtro a um ouvinte na coleção `Listeners` de uma origem de rastreamento.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`sources`|Contém as origens de rastreamento que iniciam as mensagens de rastreamento.|  
|`source`|Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.|  
|`listeners`|Especifica os ouvintes que coletam, armazenam e roteiam mensagens.|  
  
## <a name="remarks"></a>Comentários  
 As classes de ouvinte que acompanham o .NET Framework derivam o <xref:System.Diagnostics.TraceListener> classe.  
  
 Se você não especificar o `name` atributo do ouvinte de rastreamento, o <xref:System.Diagnostics.TraceListener.Name%2A> propriedade do ouvinte de rastreamento padrão é uma cadeia de caracteres vazia (""). Se seu aplicativo tiver somente um ouvinte, você pode adicioná-lo sem especificar um nome, e você pode removê-lo especificando uma cadeia de caracteres vazia para o nome. No entanto, se seu aplicativo tiver mais de um ouvinte, você deve especificar um nome exclusivo para cada ouvinte de rastreamento, que permite que você identifique e gerencie os ouvintes de rastreamento individuais a <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> coleção.  
  
> [!NOTE]
>  Adicionando mais de um ouvinte de rastreamento do mesmo tipo e com o mesmo nome resultados no ouvinte de rastreamento somente um desse tipo e nomeie o que está sendo adicionado ao `Listeners` coleção. No entanto, você pode adicionar programaticamente várias escutas idênticas a `Listeners` coleção.  
  
 O valor para o `initializeData` atributo depende do tipo de ouvinte que você cria. Nem todos os ouvintes de rastreamento requerem que você especifique `initializeData`.  
  
> [!NOTE]
>  Quando você usa o `initializeData` atributo, você pode receber o aviso "o atributo 'initializeData' não é declarado" do compilador Este aviso ocorre porque as definições de configuração são validadas em relação a classe base abstrata <xref:System.Diagnostics.TraceListener>, que não reconhece o `initializeData` atributo. Normalmente, você pode ignorar este aviso para as implementações de ouvinte de rastreamento que tem um construtor que aceita um parâmetro.  
  
 A tabela a seguir mostra os ouvintes de rastreamento que são incluídos com o .NET Framework e descreve o valor de suas `initializeData` atributos.  
  
|Classe de ouvintes de rastreamento|valor do atributo initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|O `useErrorStream` de valor para o <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> construtor.  Defina as `initializeData` de atributo para "`true`"gravar saída de rastreamento e depuração para o fluxo de erro padrão; defina-"`false`" para gravar no fluxo de saída padrão.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|O nome da origem de um log de eventos existente.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|O nome do arquivo que o <xref:System.Diagnostics.EventSchemaTraceListener> grava.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|O nome do arquivo que o <xref:System.Diagnostics.TextWriterTraceListener> grava.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|O nome do arquivo que o <xref:System.Diagnostics.XmlWriterTraceListener> grava.|  
  
## <a name="configuration-file"></a>Arquivo de Configuração  
 Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar `<add>` elementos para adicionar os ouvintes `console` e `textListener` para o `Listeners` coleção para a origem de rastreamento `TraceSourceApp`. O `textListener` ouvinte grava a saída de rastreamento para o arquivo myListener.log.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="TraceSourceApp" switchName="sourceSwitch"   
        switchType="System.Diagnostics.SourceSwitch">  
        <listeners>  
          <add name="console"   
            type="System.Diagnostics.ConsoleTraceListener"/>  
          <add name="textListener"/>  
          <remove name="Default"/>  
        </listeners>  
      </source>  
    </sources>  
    <sharedListeners>  
      <add name="textListener"   
        type="System.Diagnostics.TextWriterTraceListener"   
        initializeData="myListener.log"/>  
    </sharedListeners>  
    <switches>  
      <add name="sourceSwitch" value="Warning"/>  
    </switches>  
  </system.diagnostics>  
</configuration>   
```  
  
## <a name="see-also"></a>Consulte também

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [Esquema de configurações de rastreamento e depuração](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
- [Ouvintes de rastreamento](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
