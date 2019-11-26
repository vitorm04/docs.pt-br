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
ms.openlocfilehash: 116a9633d16b8dd36c82f07a8e727f6f9f98f0ee
ms.sourcegitcommit: 7f8eeef060ddeb2cabfa52843776faf652c5a1f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/14/2019
ms.locfileid: "74088976"
---
# <a name="add-element-for-sharedlisteners"></a>\<Adicionar > elemento para \<sharedListeners >
Adiciona um ouvinte na coleção `sharedListeners`. `sharedListeners` é uma coleção de ouvintes que qualquer [\<de > de origem](source-element.md) ou [\<> de rastreamento](trace-element.md) pode fazer referência.  Por padrão, os ouvintes na coleção de `sharedListeners` não são colocados em uma coleção de `Listeners`. Eles devem ser adicionados pelo nome ao [> de origem\<](source-element.md) ou [\<> de rastreamento](trace-element.md). Não é possível obter os ouvintes na coleção de `sharedListeners` no código em tempo de execução.  

[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<System. diagnostics >** ](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<sharedListeners**](sharedlisteners-element.md) >\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;\<**adicionar >**

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
|`name`|Atributo obrigatório.<br /><br /> Especifica o nome do ouvinte que é usado para adicionar o ouvinte compartilhado a uma coleção de `Listeners`.|  
|`type`|Atributo obrigatório.<br /><br /> Especifica o tipo do ouvinte. Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados na [especificação de nomes de tipo totalmente qualificados](../../../reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atributo opcional.<br /><br /> A cadeia de caracteres passada para o construtor para a classe especificada.|  
|`traceOutputOptions`|Atributo opcional.<br/><br/>A representação de cadeia de caracteres de um ou mais membros de enumeração <xref:System.Diagnostics.TraceOptions> que indica os dados a serem gravados na saída do rastreamento. Vários itens são separados por vírgulas. O valor padrão é "None".|

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
 As classes de ouvinte fornecidas com o .NET Framework derivam da classe <xref:System.Diagnostics.TraceListener>. O valor para o atributo `name` é usado para adicionar o ouvinte compartilhado a uma coleção de `Listeners` para um rastreamento ou uma origem de rastreamento. O valor para o atributo `initializeData` depende do tipo de ouvinte que você criar. Nem todos os ouvintes de rastreamento exigem que você especifique `initializeData`.  
  
> [!NOTE]
> Ao usar o atributo `initializeData`, você pode obter o aviso do compilador "o atributo ' initializeData ' não é declarado". Esse aviso ocorre porque as definições de configuração são validadas em relação à classe base abstrata <xref:System.Diagnostics.TraceListener>, que não reconhece o atributo `initializeData`. Normalmente, você pode ignorar esse aviso para implementações de ouvinte de rastreamento que têm um construtor que usa um parâmetro.  
  
 A tabela a seguir mostra os ouvintes de rastreamento que estão incluídos com o .NET Framework e descreve o valor de seus atributos de `initializeData`.  
  
|Classe de ouvinte de rastreamento|valor do atributo initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|O valor de `useErrorStream` para o construtor de <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A>.  Defina o atributo `initializeData` como "`true`" para gravar o rastreamento e depurar a saída para o fluxo de erro padrão; Defina-o como "`false`" para gravar no fluxo de saída padrão.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|O nome da origem de um log de eventos existente.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|O nome do arquivo no qual o <xref:System.Diagnostics.EventSchemaTraceListener> grava.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|O nome do arquivo no qual o <xref:System.Diagnostics.TextWriterTraceListener> grava.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|O nome do arquivo no qual o <xref:System.Diagnostics.XmlWriterTraceListener> grava.|  
  
## <a name="configuration-file"></a>Arquivo de Configuração  
 Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar elementos de `<add>` para adicionar o <xref:System.Diagnostics.TextWriterTraceListener>`textListener` à coleção de `sharedListeners`.   `textListener` é adicionado pelo nome à coleção de `Listeners` para o `TraceSourceApp`de origem de rastreamento. O ouvinte de `textListener` grava a saída de rastreamento no arquivo myListener. log.  
  
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
