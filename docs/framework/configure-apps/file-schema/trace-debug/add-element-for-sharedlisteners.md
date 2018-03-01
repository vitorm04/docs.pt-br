---
title: '&lt;Adicionar&gt; elemento para &lt;sharedListeners&gt;'
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
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sharedListeners/add
helpviewer_keywords:
- initializeData attribute
- <add> element for <sharedListeners>
- add element for <sharedListeners>
ms.assetid: 1595e1bc-2492-421f-8384-7f382eb8eb57
caps.latest.revision: 
author: mcleblanc
ms.author: markl
manager: markl
ms.workload:
- dotnet
ms.openlocfilehash: 490e58d4514667c5ec781dd76644012b0c97509d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="ltaddgt-element-for-ltsharedlistenersgt"></a>&lt;Adicionar&gt; elemento para &lt;sharedListeners&gt;
Adiciona um ouvinte na coleção `sharedListeners`. `sharedListeners`é uma coleção de ouvintes que quaisquer [ \<fonte >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) ou [ \<rastreamento >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md) podem fazer referência.  Por padrão, ouvintes no `sharedListeners` coleção não são colocados em um `Listeners` coleção. Eles devem ser adicionados por nome para o [ \<fonte >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/source-element.md) ou [ \<rastreamento >](../../../../../docs/framework/configure-apps/file-schema/trace-debug/trace-element.md). Não é possível obter os ouvintes de `sharedListeners` coleção no código em tempo de execução.  
  
 \<configuration>  
\<System. Diagnostics >  
\<sharedListeners > elemento  
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
|`name`|Atributo obrigatório.<br /><br /> Especifica o nome do ouvinte que é usado para adicionar o ouvinte de compartilhado para um `Listeners` coleção.|  
|`type`|Atributo obrigatório.<br /><br /> Especifica o tipo de ouvinte. Você deve usar uma cadeia de caracteres que atenda aos requisitos especificados em [especificando nomes de tipo totalmente qualificados](../../../../../docs/framework/reflection-and-codedom/specifying-fully-qualified-type-names.md).|  
|`initializeData`|Atributo opcional.<br /><br /> A cadeia de caracteres passada para o construtor para a classe especificada.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<filter>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/filter-element-for-add-for-sharedlisteners.md)|Adiciona um filtro a um ouvinte na coleção `sharedListeners`.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`sharedListeners`|Uma coleção de ouvintes que podem referenciar qualquer origem ou o elemento de rastreamento.|  
  
## <a name="remarks"></a>Comentários  
 As classes de ouvinte fornecidas com o .NET Framework derivam de <xref:System.Diagnostics.TraceListener> classe. O valor para o `name` atributo é usado para adicionar o ouvinte compartilhado para um `Listeners` coleção para um rastreamento ou uma origem de rastreamento. O valor para o `initializeData` atributo depende do tipo de ouvinte que você criar. Nem todos os ouvintes de rastreamento requerem que você especifique `initializeData`.  
  
> [!NOTE]
>  Quando você usa o `initializeData` atributo, você pode obter o compilador aviso "o atributo 'initializeData' não é declarado". Este aviso ocorre porque as definições de configuração são validadas em relação a classe base abstrata <xref:System.Diagnostics.TraceListener>, que não reconhece o `initializeData` atributo. Normalmente, você pode ignorar este aviso para implementações de ouvinte de rastreamento que tem um construtor que usa um parâmetro.  
  
 A tabela a seguir mostra os ouvintes de rastreamento que são incluídos com o .NET Framework e descreve o valor de suas `initializeData` atributos.  
  
|Classe de ouvinte de rastreamento|valor do atributo initializeData|  
|--------------------------|------------------------------------|  
|<xref:System.Diagnostics.ConsoleTraceListener>|O `useErrorStream` valor para o <xref:System.Diagnostics.ConsoleTraceListener.%23ctor%2A> construtor.  Definir o `initializeData` atributo "`true`"gravar saída de rastreamento e depuração para o fluxo de erro padrão; defina-a como"`false`" para gravar o fluxo de saída padrão.|  
|<xref:System.Diagnostics.DelimitedListTraceListener>|O nome do arquivo no qual o <xref:System.Diagnostics.DelimitedListTraceListener> é gravado.|  
|<xref:System.Diagnostics.EventLogTraceListener?displayProperty=nameWithType>|O nome da origem de um log de eventos existente.|  
|<xref:System.Diagnostics.EventSchemaTraceListener?displayProperty=nameWithType>|O nome do arquivo que o <xref:System.Diagnostics.EventSchemaTraceListener> grava.|  
|<xref:System.Diagnostics.TextWriterTraceListener?displayProperty=nameWithType>|O nome do arquivo que o <xref:System.Diagnostics.TextWriterTraceListener> grava.|  
|<xref:System.Diagnostics.XmlWriterTraceListener>|O nome do arquivo que o <xref:System.Diagnostics.XmlWriterTraceListener> grava.|  
  
## <a name="configuration-file"></a>Arquivo de Configuração  
 Esse elemento pode ser usado no arquivo de configuração de máquina (Machine. config) e o arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar `<add>` elementos para adicionar o <xref:System.Diagnostics.TextWriterTraceListener> `textListener` para o `sharedListeners` coleção.   `textListener`é adicionada pelo nome para o `Listeners` coleção para a origem de rastreamento `TraceSourceApp`. O `textListener` ouvinte grava a saída de rastreamento para o arquivo myListener.log.  
  
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
 <xref:System.Diagnostics.TraceSource>  
 <xref:System.Diagnostics.TraceListener>  
 [Esquema de configurações de rastreamento e depuração](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)  
 [Ouvintes de rastreamento](../../../../../docs/framework/debug-trace-profile/trace-listeners.md)
