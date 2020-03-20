---
title: Elemento <source>
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 417722ce2f3865350158413307495e3ab435d386
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79153289"
---
# <a name="source-element"></a>\<origem> Elemento
Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.  

[**\<>de configuração**](../configuration-element.md)\
&nbsp;&nbsp;[**\<system.diagnostics>**](system-diagnostics-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[**\<fontes>**](sources-element.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;**\<>fonte**

## <a name="syntax"></a>Sintaxe  
  
```xml  
<source>
  <listeners>...</listeners>  
</source>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|`name`|Atributo opcional.<br /><br /> Especifica o nome da fonte de rastreamento.|  
|`switchName`|Atributo opcional.<br /><br /> Especifica o nome de uma instância de switch de rastreamento no aplicativo. Se o switch não `<switches>` for identificado em um elemento, o valor especificará o nível do switch.|  
|`switchType`|Atributo opcional.<br /><br /> Especifica o tipo do interruptor de rastreamento. Se estiver presente, o tipo deve ser um nome de classe válido e não pode ser uma seqüência de string vazia.|  
|`extraAttribute`|Atributo opcional.<br /><br /> Especifica o valor de um atributo específico <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> da origem de rastreamento identificado pelo método para essa fonte de rastreamento.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<ouvintes>](listeners-element-for-source.md)|Contém ouvintes que coletam, armazenam e encaminham mensagens.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`sources`|Contém as origens de rastreamento que iniciam as mensagens de rastreamento.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento pode ser usado no arquivo de configuração da máquina (Machine.config) e no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir `<source>` mostra como usar `mySource` o elemento para adicionar a `sourceSwitch`fonte de rastreamento e definir o nível para o switch de origem chamado . Um ouvinte de rastreamento de console é adicionado que grava informações de rastreamento para o console.  
  
```xml  
<configuration>  
  <system.diagnostics>  
    <sources>  
      <source name="mySource" switchName="sourceSwitch" switchType="System.Diagnostics.SourceSwitch"  >  
        <listeners>  
          <add name="console" type="System.Diagnostics.ConsoleTraceListener" >  
            <filter type="System.Diagnostics.EventTypeFilter" initializeData="Error" />  
          </add>  
          <remove name="Default" />  
        </listeners>  
      </source>  
    </sources>  
        <switches>  
           <add name="sourceSwitch" value="Warning" />  
        </switches>
  </system.diagnostics>
</configuration>  
```  
  
## <a name="see-also"></a>Confira também

- [Esquema de configurações de rastreamento e depuração](index.md)
- [Opções de rastreamento](../../../debug-trace-profile/trace-switches.md)
