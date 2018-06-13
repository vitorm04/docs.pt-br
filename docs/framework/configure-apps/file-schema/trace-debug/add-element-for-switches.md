---
title: '&lt;Adicionar&gt; elemento para &lt;switches&gt;'
ms.date: 03/30/2017
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches/add
helpviewer_keywords:
- <add> element for <switches>
- add element for <switches>
ms.assetid: 712ac3a7-7abf-4a9e-8db4-acd241c2f369
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: e0dc425327f6577606e1205a23fdaffcc39f6e01
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32747448"
---
# <a name="ltaddgt-element-for-ltswitchesgt"></a>&lt;Adicionar&gt; elemento para &lt;switches&gt;
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
|**name**|Atributo obrigatório.<br /><br /> Especifica o nome do comutador. O valor deste atributo corresponde do *displayName* parâmetro que é passado para a opção construtor.|  
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
 Você pode alterar o nível de um comutador de rastreamento, colocando-o em um arquivo de configuração. Se a opção é uma <xref:System.Diagnostics.BooleanSwitch>, você pode ativar e desativar. Se a opção é uma <xref:System.Diagnostics.TraceSwitch>, você pode atribuir diferentes níveis-o para especificar os tipos de rastreamento ou as saídas de aplicativo de mensagens de depuração.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o  **\<Adicionar >** elemento para definir o `General` alternar de rastreamento para o <xref:System.Diagnostics.TraceLevel> nível e habilitar o `Data` opção trace Boolean.  
  
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
