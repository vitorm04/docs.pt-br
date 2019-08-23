---
title: Elemento <source>
ms.date: 09/29/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/sources/source
- http://schemas.microsoft.com/.NetConfiguration/v2.0#source
helpviewer_keywords:
- <source> element
- source element
ms.openlocfilehash: 55120e292ac2a2c822c5510563d1aa167ca921e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69920450"
---
# <a name="source-element"></a>\<Elemento de > de origem
Especifica uma origem de rastreamento que inicia as mensagens de rastreamento.  
  
 \<configuration>  
\<System. Diagnostics >  
\<fontes >  
\<> de origem  
  
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
|`name`|Atributo opcional.<br /><br /> Especifica o nome da origem do rastreamento.|  
|`switchName`|Atributo opcional.<br /><br /> Especifica o nome de uma instância de opção de rastreamento no aplicativo. Se a opção não for identificada em `<switches>` um elemento, o valor especificará o nível para a opção.|  
|`switchType`|Atributo opcional.<br /><br /> Especifica o tipo da opção de rastreamento. Se presente, o tipo deve ser um nome de classe válido e não pode ser uma cadeia de caracteres vazia.|  
|`extraAttribute`|Atributo opcional.<br /><br /> Especifica o valor para um atributo específico de origem de rastreamento identificado pelo <xref:System.Diagnostics.TraceSource.GetSupportedAttributes%2A> método para essa origem de rastreamento.|  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<listeners>](listeners-element-for-source.md)|Contém ouvintes que coletam, armazenam e roteiam mensagens.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
|`sources`|Contém as origens de rastreamento que iniciam as mensagens de rastreamento.|  
  
## <a name="remarks"></a>Comentários  
 Esse elemento pode ser usado no arquivo de configuração da máquina (Machine. config) e no arquivo de configuração do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o `<source>` elemento para adicionar a origem `mySource` de rastreamento e definir o nível para a opção de origem `sourceSwitch`denominada. Um ouvinte de rastreamento de console é adicionado que grava informações de rastreamento no console do.  
  
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
  
## <a name="see-also"></a>Consulte também

- [Esquema de configurações de rastreamento e depuração](index.md)
- [Opções de rastreamento](../../../debug-trace-profile/trace-switches.md)
