---
title: <routing> de <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: 0998f4fc61de7099879ba6e122eed1e64588baec
ms.sourcegitcommit: 093571de904fc7979e85ef3c048547d0accb1d8a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/06/2019
ms.locfileid: "70397726"
---
# <a name="routing-of-servicebehavior"></a>\<> de roteamento \<de > de serviço
Fornece acesso de tempo de execução ao serviço de roteamento para permitir a modificação dinâmica da configuração de roteamento.  
  
[ **\<configuration>** ](../configuration-element.md)\
&nbsp;&nbsp;[ **\<> de System. serviceModel**](system-servicemodel.md)\
&nbsp;&nbsp;&nbsp;&nbsp;[ **\<comportamentos >** ](behaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de portais**](servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;[ **\<> de comportamento**](behavior-of-servicebehaviors.md)\
&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp;&nbsp; **\<> de roteamento**  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<behaviors>
  <serviceBehaviors>
    <behavior name="String">
      <routing filterTable="String"
               routeOnHeadersOnly="Boolean"
               SoapProcessingEnabled="Boolean" />
    </behavior>
  </serviceBehaviors>
</behaviors>
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|filterTable|Uma cadeia de caracteres que especifica o nome da tabela de roteamento que contém filtros a serem avaliados pelo serviço de roteamento. Esse valor deve corresponder ao `name` atributo de um [ \<elemento de > de FilterTable](filtertable.md) na seção de [ \<> filterTables](filtertables.md) .|  
|routeOnHeaderOnly|Um valor booliano que especifica se o filtro examinará o corpo da mensagem e o cabeçalho, ou apenas o cabeçalho. O padrão é `true`.|  
|soapProcessingEnabled|Um valor booliano que especifica se o processamento SOAP deve ocorrer.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<> de comportamento](behavior-of-endpointbehaviors.md)|Especifica um elemento de comportamento.|  
  
## <a name="remarks"></a>Comentários  
 Quando adicionado à configuração de comportamento do serviço, esse elemento de configuração habilita o roteamento para o serviço. Você pode especificar a tabela de roteamento real a ser usada pelo serviço neste elemento.  
  
 Usando esta seção de configuração, você pode alterar suas configurações de roteamento imediatamente quando o padrão de implantação for alterado. Em tempo de execução, você pode registrar sua própria extensão de roteamento com novas configurações de roteamento e o serviço de roteamento começará a usar as informações de configuração atualizadas para novas mensagens e sessões, deixando de manter mensagens/sessões em andamento usando quaisquer regras que estavam em local quando eles começaram.  Isso lhe dá a capacidade de fazer a reconfiguração com segurança de sessão e sem reciclagem do serviço de roteamento durante o tempo de execução.  
