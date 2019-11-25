---
title: <add> elemento para <listeners> para <source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: c32205310f9fc451a5a55a943f925ee52f65c8a8
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088997"
---
# <a name="add-element-for-listeners-for-source"></a>\<Adicionar > elemento para \<ouvintes > para \<fonte >
Adiciona um ouvinte na coleção `Listeners` de uma origem de rastreamento.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;\<[**fontes**](sources-element.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**fonte >** ](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<[**ouvintes**](listeners-element-for-source.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<adicionar >**

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
|`type`|Atributo obrigatório, a menos que você esteja fazendo referência a um ouvinte na coleção de `sharedListeners`; nesse caso, você só precisa fazer referência a ele por nome (consulte o [exemplo](#example)).<br /><br /> Especifica o tipo do ouvinte. Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados na [especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atributo opcional.<br /><br /> A cadeia de caracteres passada para o construtor para a classe especificada. Um <xref:System.Configuration.ConfigurationException> será gerado se a classe não tiver um construtor que usa uma cadeia de caracteres.|  
|`name`|Atributo opcional.<br /><br /> Especifica o nome do ouvinte.|  
|`traceOutputOptions`|Atributo opcional.<br /><br /> Especifica o valor da propriedade de <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> para o ouvinte de rastreamento.|  
|[atributos personalizados]|Atributos opcionais.<br /><br /> Especifica o valor para atributos específicos do ouvinte identificados pelo método <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> para esse ouvinte. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A> é um exemplo de um atributo extra exclusivo para a classe <xref:System.Diagnostics.DelimitedListTraceListener>.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-listeners-for-source.md)|Adiciona um filtro a um ouvinte na coleção `Listeners` de uma origem de rastreamento.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`sources`|Contém as origens de rastreamento que iniciam as mensagens de rastreamento.|  
|`source`|Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.|  
|`listeners`|Especifica os ouvintes que coletam, armazenam e roteiam mensagens.|  
  
## <a name="remarks"></a>Comentários  
 As classes de ouvinte fornecidas com o .NET Framework derivam da classe <xref:System.Diagnostics.TraceListener>.  
  
 Se você não especificar o atributo `name` do ouvinte de rastreamento, a propriedade <xref:System.Diagnostics.TraceListener.Name%2A> do ouvinte de rastreamento será padronizada como uma cadeia de caracteres vazia (""). Se seu aplicativo tiver apenas um ouvinte, você poderá adicioná-lo sem especificar um nome, e poderá removê-lo especificando uma cadeia de caracteres vazia para o nome. No entanto, se seu aplicativo tiver mais de um ouvinte, você deverá especificar um nome exclusivo para cada ouvinte de rastreamento, que permite identificar e gerenciar ouvintes de rastreamento individuais na coleção de <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType>.  
  
> [!NOTE]
> Adicionar mais de um ouvinte de rastreamento do mesmo tipo e com o mesmo nome resulta em apenas um ouvinte de rastreamento desse tipo e nome que estão sendo adicionados à coleção de `Listeners`. No entanto, você pode adicionar programaticamente vários ouvintes idênticos à coleção de `Listeners`.  
  
 O valor para o atributo `initializeData` depende do tipo de ouvinte que você criar. Nem todos os ouvintes de rastreamento exigem que você especifique `initializeData`.  
  
> [!NOTE]
> Ao usar o atributo `initializeData`, você pode obter o aviso do compilador "o atributo ' initializeData ' não é declarado". Esse aviso ocorre porque as definições de configuração são validadas em relação à classe base abstrata <xref:System.Diagnostics.TraceListener>, que não reconhece o atributo `initializeData`. Normalmente, você pode ignorar esse aviso para implementações de ouvinte de rastreamento que têm um construtor que usa um parâmetro.  
  
 A tabela a seguir mostra os ouvintes de rastreamento que estão incluídos com o .NET Framework e descreve o valor de seus atributos de `initializeData`.  
  
|Classe de ouvinte de rastreamento|valor do atributo initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|O valor de `useErrorStream` para o construtor de <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>.  Defina o atributo `initializeData` como "`true`" para gravar o rastreamento e depurar a saída para o fluxo de erro padrão; Defina-o como "`false`" para gravar no fluxo de saída padrão.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|O nome da origem de um log de eventos existente.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|O nome do arquivo no qual o <xref:System.Diagnostics.EventSchemaTraceListener> grava.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|O nome do arquivo no qual o <xref:System.Diagnostics.TextWriterTraceListener> grava.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|O nome do arquivo no qual o <xref:System.Diagnostics.XmlWriterTraceListener> grava.|  
  
## <a name="configuration-file"></a>Arquivo de Configuração  
 Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar os elementos de `<add>` para adicionar os ouvintes `console` e `textListener` à coleção de `Listeners` para a `TraceSourceApp`de origem de rastreamento. O ouvinte de `textListener` grava a saída de rastreamento no arquivo myListener. log.  
  
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
- [Esquema de configurações de rastreamento e depuração](index.md)
- [Ouvintes de rastreamento](../../../debug-trace-profile/trace-listeners.md)
