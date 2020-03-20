---
title: <add>Elemento <listeners> para para<source>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source/listeners/add
helpviewer_keywords:
- initializeData attribute
- add element for <listeners> for <source>
- <add> element for <listeners> for <source>
ms.assetid: 4ce36ac1-81ef-48e8-b8b2-b5a5b0e2adcb
ms.openlocfilehash: 883eef32172c5a7f900197995b4c57c3d5a84e19
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153679"
---
# <a name="add-element-for-listeners-for-source"></a>\<adicionar> \<Element para \<ouvintes> para> de origem
Adiciona um ouvinte na coleção `Listeners` de uma origem de rastreamento.  

[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<fontes>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<>fonte**](source-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[**\<ouvintes>**](listeners-element-for-source.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<adicionar>**

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
|`type`|Atributo necessário, a menos que você `sharedListeners` esteja fazendo referência a um ouvinte na coleção, nesse caso você só precisa se referir a ele pelo nome (veja o [Exemplo](#example)).<br /><br /> Especifica o tipo do ouvinte. Você deve usar uma string que atenda aos requisitos especificados na [Especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atributo opcional.<br /><br /> A seqüência passou para o construtor para a classe especificada. A <xref:System.Configuration.ConfigurationException> é jogado se a classe não tem um construtor que leva uma corda.|  
|`name`|Atributo opcional.<br /><br /> Especifica o nome do ouvinte.|  
|`traceOutputOptions`|Atributo opcional.<br /><br /> Especifica o <xref:System.Diagnostics.TraceListener.TraceOutputOptions%2A> valor da propriedade para o ouvinte de rastreamento.|  
|[atributos personalizados]|Atributos opcionais.<br /><br /> Especifica o valor para atributos específicos <xref:System.Diagnostics.TraceListener.GetSupportedAttributes%2A> do ouvinte identificados pelo método para esse ouvinte. <xref:System.Diagnostics.DelimitedListTraceListener.Delimiter%2A>é um exemplo de um <xref:System.Diagnostics.DelimitedListTraceListener> atributo extra único para a classe.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de filtro](filter-element-for-add-for-listeners-for-source.md)|Adiciona um filtro a um ouvinte na coleção `Listeners` de uma origem de rastreamento.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`sources`|Contém as origens de rastreamento que iniciam as mensagens de rastreamento.|  
|`source`|Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.|  
|`listeners`|Especifica os ouvintes que coletam, armazenam e encaminham mensagens.|  
  
## <a name="remarks"></a>Comentários  
 As classes de ouvinte enviadas com o <xref:System.Diagnostics.TraceListener> Quadro .NET derivam da classe.  
  
 Se você não `name` especificar o atributo <xref:System.Diagnostics.TraceListener.Name%2A> do ouvinte de rastreamento, a propriedade do ouvinte de rastreamento será padrão para uma seqüência de string vazia (""). Se o aplicativo tiver apenas um ouvinte, você pode adicioná-lo sem especificar um nome e removê-lo especificando uma seqüência de string vazia para o nome. No entanto, se o seu aplicativo tiver mais de um ouvinte, você deve especificar um nome <xref:System.Diagnostics.TraceSource.Listeners%2A?displayProperty=nameWithType> único para cada ouvinte de rastreamento, o que permite identificar e gerenciar ouvintes de rastreamento individuais na coleção.  
  
> [!NOTE]
> Adicionar mais de um ouvinte de rastreamento do mesmo tipo e com o mesmo nome resulta `Listeners` em apenas um ouvinte de rastreamento desse tipo e nome sendo adicionado à coleção. No entanto, você pode adicionar programáticamente vários ouvintes idênticos à `Listeners` coleção.  
  
 O valor `initializeData` para o atributo depende do tipo de ouvinte que você cria. Nem todos os ouvintes `initializeData`de rastreamento exigem que você especifique .  
  
> [!NOTE]
> Quando você `initializeData` usa o atributo, você pode obter o aviso do compilador "O atributo 'initializeData' não é declarado." Esse aviso ocorre porque as configurações são <xref:System.Diagnostics.TraceListener>validadas em `initializeData` relação à classe base abstrata, que não reconhece o atributo. Normalmente, você pode ignorar este aviso para implementações de ouvintes de rastreamento que tenham um construtor que leva um parâmetro.  
  
 A tabela a seguir mostra os ouvintes de rastreamento que estão `initializeData` incluídos no Quadro .NET e descreve o valor de seus atributos.  
  
|Classe de ouvinte de rastreamento|inicializarvalor do atributoData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener?displayProperty=nameWithType>|O `useErrorStream` valor <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> para o construtor.  Defina `initializeData` o`true`atributo como " " para gravar a saída de rastreamento e depuração para o fluxo de erro padrão; configurá-lo`false`para " " para escrever para o fluxo de saída padrão.|  
|<xref:System.Diagnostics.DelimitedListTraceListener?displayProperty=nameWithType>|O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|O nome da origem de um log de eventos existente.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|O nome do arquivo <xref:System.Diagnostics.EventSchemaTraceListener> para o que ele escreve.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|O nome do arquivo <xref:System.Diagnostics.TextWriterTraceListener> para o que ele escreve.|  
|<xref:System.Diagnostics.XmlWriterTraceListener?displayProperty=nameWithType>|O nome do arquivo <xref:System.Diagnostics.XmlWriterTraceListener> para o que ele escreve.|  
  
## <a name="configuration-file"></a>Arquivo de configuração  
 Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir `<add>` mostra como `console` usar `textListener` elementos para adicionar os ouvintes e à `Listeners` coleção para a fonte `TraceSourceApp`de rastreamento . O `textListener` ouvinte grava a saída de rastreamento para o arquivo myListener.log.  
  
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
  
## <a name="see-also"></a>Confira também

- <xref:System.Diagnostics.TraceSource>
- <xref:System.Diagnostics.TraceListener>
- [Esquema de configurações de rastreamento e depuração](index.md)
- [Ouvintes de rastreamento](../../../debug-trace-profile/trace-listeners.md)
