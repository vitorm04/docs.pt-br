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
ms.openlocfilehash: c4b83834fb7aaf64a696b85bd2c8da47cfba2397
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69927198"
---
# <a name="add-element-for-sharedlisteners"></a>\<Adicionar > elemento para \<sharedListeners >
Adiciona um ouvinte na coleção `sharedListeners`. `sharedListeners`é uma coleção de ouvintes que qualquer [ \<> de origem](source-element.md) ou [ \<rastreamento >](trace-element.md) pode referenciar.  Por padrão, os `sharedListeners` ouvintes na coleção não são colocados em uma `Listeners` coleção. Eles devem ser adicionados pelo nome ao > [ \<](source-element.md) de [ \<rastreamento](trace-element.md)ou > de origem. Não é possível obter os ouvintes na `sharedListeners` coleção no código em tempo de execução.  
  
 \<configuration>  
&nbsp;&nbsp;\<System. Diagnostics >  
&nbsp;&nbsp;&nbsp;&nbsp;\<Elemento de > de sharedListeners  
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<add>  
  
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
|`name`|Atributo obrigatório.<br /><br /> Especifica o nome do ouvinte que é usado para adicionar o ouvinte compartilhado a `Listeners` uma coleção.|  
|`type`|Atributo obrigatório.<br /><br /> Especifica o tipo do ouvinte. Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados na [especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atributo opcional.<br /><br /> A cadeia de caracteres passada para o construtor para a classe especificada.|  
|`traceOutputOptions`|Atributo opcional.<br/><br/>A representação de cadeia de caracteres de <xref:System.Diagnostics.TraceOptions> um ou mais membros de enumeração que indica os dados a serem gravados na saída do rastreamento. Vários itens são separados por vírgulas. O valor padrão é "None".|

### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<filter>](filter-element-for-add-for-sharedlisteners.md)|Adiciona um filtro a um ouvinte na coleção `sharedListeners`.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`sharedListeners`|Uma coleção de ouvintes que qualquer elemento de origem ou de rastreamento pode referenciar.|  
  
## <a name="remarks"></a>Comentários  
 As classes de ouvinte fornecidas com o .NET Framework derivam da <xref:System.Diagnostics.TraceListener> classe. O valor para o `name` atributo é usado para adicionar o ouvinte compartilhado a `Listeners` uma coleção para um rastreamento ou uma origem de rastreamento. O valor para o `initializeData` atributo depende do tipo de ouvinte que você criar. Nem todos os ouvintes de rastreamento exigem que `initializeData`você especifique.  
  
> [!NOTE]
> Ao usar o `initializeData` atributo, você pode obter o aviso do compilador "o atributo ' initializeData ' não está declarado." Esse aviso ocorre porque as definições de configuração são validadas em relação à <xref:System.Diagnostics.TraceListener>classe base abstrata, que não `initializeData` reconhece o atributo. Normalmente, você pode ignorar esse aviso para implementações de ouvinte de rastreamento que têm um construtor que usa um parâmetro.  
  
 A tabela a seguir mostra os ouvintes de rastreamento que estão incluídos com o .NET Framework e descreve o valor `initializeData` de seus atributos.  
  
|Classe de ouvinte de rastreamento|valor do atributo initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|O `useErrorStream` valor<xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> do construtor.  Defina o `initializeData` atributo como "`true`" para gravar rastreamento e depurar saída para o fluxo de erro padrão; defina-o`false`como "" para gravar no fluxo de saída padrão.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|O nome da origem de um log de eventos existente.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|O nome do arquivo no qual as <xref:System.Diagnostics.EventSchemaTraceListener> gravações são gravadas.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|O nome do arquivo no qual as <xref:System.Diagnostics.TextWriterTraceListener> gravações são gravadas.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|O nome do arquivo no qual as <xref:System.Diagnostics.XmlWriterTraceListener> gravações são gravadas.|  
  
## <a name="configuration-file"></a>Arquivo de Configuração  
 Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar `<add>` elementos para adicionar o <xref:System.Diagnostics.TextWriterTraceListener> `textListener` à `sharedListeners` coleção.   `textListener`é adicionado pelo nome à `Listeners` coleção para a origem `TraceSourceApp`do rastreamento. O `textListener` ouvinte grava a saída de rastreamento no arquivo myListener. log.  
  
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
