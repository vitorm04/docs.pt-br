---
title: Elemento <add> para <sharedListeners>
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
ms.openlocfilehash: 5588892ec75a791eda1eb043936c0af95e79354e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153601"
---
# <a name="add-element-for-sharedlisteners"></a>\<adicionar> \<Elemento para> de ouvintes compartilhados
Adiciona um ouvinte na coleção `sharedListeners`. `sharedListeners`é uma coleção de [ \<](source-element.md) ouvintes que qualquer fonte>ou [ \<traçar>](trace-element.md) pode referenciar.  Por padrão, os `sharedListeners` ouvintes da `Listeners` coleção não são colocados em uma coleção. Eles devem ser adicionados [ \<](source-element.md) pelo nome à fonte>ou [ \<traçar>](trace-element.md). Não é possível obter os `sharedListeners` ouvintes da coleção em código em tempo de execução.  

[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<>de ouvintes compartilhados**](sharedlisteners-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<adicionar>**

## <a name="syntax"></a>Sintaxe  
  
```xml  
<add name="name"
  type="TraceListenerClassName, Version, Culture, PublicKeyToken"  
  initializeData="data"
  traceOutputOptions = "None"
/>  
```
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`name`|Atributo obrigatório.<br /><br /> Especifica o nome do ouvinte que é usado para adicionar `Listeners` o ouvinte compartilhado a uma coleção.|  
|`type`|Atributo obrigatório.<br /><br /> Especifica o tipo do ouvinte. Você deve usar uma string que atenda aos requisitos especificados na [Especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atributo opcional.<br /><br /> A seqüência passou para o construtor para a classe especificada.|  
|`traceOutputOptions`|Atributo opcional.<br/><br/>A representação de <xref:System.Diagnostics.TraceOptions> seqüência de um ou mais membros de enumeração que indica os dados a serem gravados na saída de rastreamento. Vários itens são separados por commas. O valor padrão é "Nenhum".|

### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<>de filtro](filter-element-for-add-for-sharedlisteners.md)|Adiciona um filtro a um ouvinte na coleção `sharedListeners`.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`sharedListeners`|Uma coleção de ouvintes que qualquer fonte ou elemento de rastreamento pode referenciar.|  
  
## <a name="remarks"></a>Comentários  
 As classes de ouvinte enviadas com o <xref:System.Diagnostics.TraceListener> Quadro .NET derivam da classe. O valor `name` para o atributo é usado para `Listeners` adicionar o ouvinte compartilhado a uma coleção para um traço ou uma fonte de rastreamento. O valor `initializeData` para o atributo depende do tipo de ouvinte que você cria. Nem todos os ouvintes `initializeData`de rastreamento exigem que você especifique .  
  
> [!NOTE]
> Quando você `initializeData` usa o atributo, você pode obter o aviso do compilador "O atributo 'initializeData' não é declarado." Esse aviso ocorre porque as configurações são <xref:System.Diagnostics.TraceListener>validadas em `initializeData` relação à classe base abstrata, que não reconhece o atributo. Normalmente, você pode ignorar este aviso para implementações de ouvintes de rastreamento que tenham um construtor que leva um parâmetro.  
  
 A tabela a seguir mostra os ouvintes de rastreamento que estão `initializeData` incluídos no Quadro .NET e descreve o valor de seus atributos.  
  
|Classe de ouvinte de rastreamento|inicializarvalor do atributoData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|O `useErrorStream` valor <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> para o construtor.  Defina `initializeData` o`true`atributo como " " para gravar a saída de rastreamento e depuração para o fluxo de erro padrão; configurá-lo`false`para " " para escrever para o fluxo de saída padrão.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|O nome da origem de um log de eventos existente.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|O nome do arquivo <xref:System.Diagnostics.EventSchemaTraceListener> para o que ele escreve.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|O nome do arquivo <xref:System.Diagnostics.TextWriterTraceListener> para o que ele escreve.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|O nome do arquivo <xref:System.Diagnostics.XmlWriterTraceListener> para o que ele escreve.|  
  
## <a name="configuration-file"></a>Arquivo de configuração  
 Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir `<add>` mostra como <xref:System.Diagnostics.TextWriterTraceListener> `textListener` usar `sharedListeners` elementos para adicionar à coleção.   `textListener`é adicionado por `Listeners` nome à coleção `TraceSourceApp`para a fonte de rastreamento . O `textListener` ouvinte grava a saída de rastreamento para o arquivo myListener.log.  
  
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
