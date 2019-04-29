---
title: <routing> de <serviceBehavior>
ms.date: 03/30/2017
ms.assetid: d8f9c844-4629-4a45-9599-856dc8f01794
ms.openlocfilehash: b7a9be18395ef8878900d754b5aa5afdeee0cff8
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61783052"
---
# <a name="routing-of-servicebehavior"></a>\<roteamento > de \<serviceBehavior >
Fornece acesso de tempo de execução ao serviço de roteamento para permitir a modificação dinâmica da configuração de roteamento.  
  
 \<system.ServiceModel>  
\<comportamentos >  
\<serviceBehaviors>  
\<behavior>  
\<routing>  
  
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
|filterTable|Uma cadeia de caracteres que especifica o nome da tabela de roteamento que contém os filtros a ser avaliada pelo serviço de roteamento. Esse valor deve corresponder a `name` atributo de um [ \<filterTable >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertable.md) elemento no [ \<filterTables >](../../../../../docs/framework/configure-apps/file-schema/wcf/filtertables.md) seção.|  
|routeOnHeaderOnly|Um valor booliano que especifica se o filtro examinará o corpo da mensagem e o cabeçalho ou apenas o cabeçalho. O padrão é `true`.|  
|soapProcessingEnabled|Um valor booliano que especifica se o processamento SOAP deve ocorrer.|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<behavior>](../../../../../docs/framework/configure-apps/file-schema/wcf/behavior-of-endpointbehaviors.md)|Especifica um elemento de comportamento.|  
  
## <a name="remarks"></a>Comentários  
 Quando adicionado à configuração de comportamento do serviço, este elemento de configuração permite que o roteamento para o serviço. Você pode especificar a tabela de roteamento real a ser usado pelo serviço nesse elemento.  
  
 Usando essa seção de configuração, você pode alterar suas configurações de roteamentos em tempo real quando seu padrão de implantação é alterado. Em tempo de execução, você pode registrar sua própria extensão de roteamento com novas configurações de roteamentos e o serviço de roteamento começarão a usar as informações de configuração atualizados para novas mensagens e sessões, deixando as mensagens em trânsito/sessões usando as regras que estavam em Coloque quando foram iniciados.  Isso lhe dá a capacidade de fazer a reconfiguração de sessão segura, sem a reciclagem do serviço de roteamento de durante o tempo de execução.  
