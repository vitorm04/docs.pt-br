---
title: '&lt;Adicione&gt; elemento para &lt;switches&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
author: mcleblanc
ms.author: markl
ms.openlocfilehash: 0a1a2c9ec34c43eb1b9559d90a8da0d70193c19e
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47109518"
---
# <a name="ltaddgt-element-for-ltswitchesgt"></a>&lt;Adicione&gt; elemento para &lt;switches&gt;
Especifica o nível em que uma opção de rastreamento é definida.  
  
 \<configuration>  
\<System. Diagnostics >  
\<Switches >  
\<add>  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<add name="switch name"  
     value="value"/>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|**name**|Atributo obrigatório.<br /><br /> Especifica o nome do comutador. O valor desse atributo corresponde à *displayName* parâmetro que é passado para alternar o construtor.|  
|**value**|Atributo obrigatório.<br /><br /> Especifica o nível do comutador.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`switches`|Contém opções de rastreamento e o nível em que as opções de rastreamento são definidas.|  
|`system.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
  
## <a name="remarks"></a>Comentários  
 Você pode alterar o nível de uma opção de rastreamento, colocando-o em um arquivo de configuração. Se a opção é um <xref:System.Diagnostics.BooleanSwitch>, você pode ativar e desativar. Se a opção é um <xref:System.Diagnostics.TraceSwitch>, você pode atribuir diferentes níveis a ele para especificar os tipos de rastreamento ou depuração mensagens as saídas do aplicativo.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o  **\<Adicionar >** elemento para definir a `General` opção de rastreamento para o <xref:System.Diagnostics.TraceLevel> nível e habilitar o `Data` opção de rastreamento Boolean.  
  
```xml  
<configuration>  
   <system.diagnostics>  
      <switches>  
         <add name="General" value="4" />  
         <add name="Data" value="1" />  
      </switches>  
   </system.diagnostics>  
</configuration>  
```  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Diagnostics.Switch>  
 <xref:System.Diagnostics.TraceSwitch>  
 <xref:System.Diagnostics.BooleanSwitch>  
 [Esquema de configurações de rastreamento e depuração](../../../../../docs/framework/configure-apps/file-schema/trace-debug/index.md)
