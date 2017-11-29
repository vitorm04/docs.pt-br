---
title: '&lt;comutadores&gt; elemento'
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- http://schemas.microsoft.com/.NetConfiguration/v2.0#configuration/system.diagnostics/switches
- http://schemas.microsoft.com/.NetConfiguration/v2.0#switches
helpviewer_keywords:
- <switches> element
- switches element
- trace switches, <switches> element
ms.assetid: 4cf36786-b89a-40e2-a0f1-86bb9b783343
caps.latest.revision: "11"
author: mcleblanc
ms.author: markl
manager: markl
ms.openlocfilehash: 6240f8192f2a31faeb81528e54481eb06cc04d04
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="ltswitchesgt-element"></a>&lt;comutadores&gt; elemento
Contém opções de rastreamento e o nível em que as opções de rastreamento são definidas.  
  
 \<configuration>  
\<System. Diagnostics >  
\<Switches >  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
      <switches>   
</switches>  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
 nenhuma.  
  
### <a name="child-elements"></a>Elementos filho  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<add>](../../../../../docs/framework/configure-apps/file-schema/trace-debug/add-element-for-switches.md)|Especifica o nível em que uma opção de rastreamento é definida.|  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|`configuration`|O elemento raiz em cada arquivo de configuração usado pelos aplicativos do Common Language Runtime e .NET Framework.|  
|`System.diagnostics`|Especifica os ouvintes de rastreamento que coletam, armazenam e roteiam mensagens e o nível em que uma opção de rastreamento é definida.|  
  
## <a name="remarks"></a>Comentários  
 Você pode alterar o nível de um comutador de rastreamento, colocando-o em um arquivo de configuração. Se a opção é uma <xref:System.Diagnostics.BooleanSwitch>, você pode ativar e desativar. Se a opção é uma <xref:System.Diagnostics.TraceSwitch>, você pode atribuir diferentes níveis-o para especificar os tipos de rastreamento ou as saídas de aplicativo de mensagens de depuração.  
  
## <a name="example"></a>Exemplo  
 O exemplo a seguir mostra como usar o  **\<alternar >** elemento para definir o `General` alternar de rastreamento para o <xref:System.Diagnostics.TraceLevel> nível e habilitar o `Data` opção trace Boolean.  
  
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
