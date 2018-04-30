---
title: '&lt;parameter&gt;'
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0fb41e2d-64f7-44ab-993e-05892eac6d82
caps.latest.revision: 9
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: aa4b2c870864a4359ebca0a1ae47fc1c8aaebca0
ms.sourcegitcommit: 94d33cadc5ff81d2ac389bf5f26422c227832052
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/30/2018
---
# <a name="ltparametergt"></a>&lt;parameter&gt;
Especifica o parâmetro genérico quando um tipo declarado é um tipo genérico.  
  
 \<Serialization >  
\<dataContractSerializer >  
\<declaredTypes > elemento  
\<Adicionar > elemento para \<declaredTypes >  
\<knownType > elemento  
\<parâmetro > elemento  
  
## <a name="syntax"></a>Sintaxe  
  
```xml  
<parameter index="integer"  
                      type=String" />  
```  
  
## <a name="attributes-and-elements"></a>Atributos e elementos  
 As seções a seguir descrevem atributos, elementos filho e elementos pai.  
  
### <a name="attributes"></a>Atributos  
  
|Atributo|Descrição|  
|---------------|-----------------|  
|índice|Quando o tipo declarado é um tipo genérico, especifica o parâmetro genérico que retornará o tipo conhecido.|  
|tipo|Uma cadeia de caracteres que descreve o tipo conhecido usado para serialização e desserialização.|  
  
## <a name="index-attribute"></a>Atributo de índice  
  
|Valor|Descrição|  
|-----------|-----------------|  
|"0"|O primeiro parâmetro de tipo genérico. Por exemplo, um <xref:System.Collections.Generic.List%601> tem apenas um parâmetro. Se ele é usado como o tipo declarado, o índice seria definido como "0".|  
|"1"|O segundo parâmetro em um tipo genérico. Por exemplo, um <xref:System.Collections.Generic.Dictionary%602> tem dois parâmetros. Se o tipo conhecido é retornado pelo segundo parâmetro, defina o atributo de índice como "1".|  
  
### <a name="child-elements"></a>Elementos filho  
 nenhuma.  
  
### <a name="parent-elements"></a>Elementos pai  
  
|Elemento|Descrição|  
|-------------|-----------------|  
|[\<knownType >](../../../../../docs/framework/configure-apps/file-schema/wcf/knowntype.md)|Especifica um tipo conhecido que pode ser retornado por um campo ou propriedade do tipo declarado.|  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre tipos conhecidos, consulte [tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md) e <xref:System.Runtime.Serialization.DataContractSerializer>.  
  
 Consulte o [ \<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md) para obter um exemplo de como usar esse elemento.  
  
 Este elemento de configuração não pode ter dois atributos ao mesmo tempo. Se ambos os atributos são definidos, um <xref:System.Configuration.ConfigurationErrorsException> ocorre.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Runtime.Serialization.DataContractSerializer>  
 [Tipos conhecidos de contrato de dados](../../../../../docs/framework/wcf/feature-details/data-contract-known-types.md)  
 [\<dataContractSerializer >](../../../../../docs/framework/configure-apps/file-schema/wcf/datacontractserializer-element.md)  
 [\<add>](../../../../../docs/framework/configure-apps/file-schema/wcf/add-of-declaredtypes-element.md)
