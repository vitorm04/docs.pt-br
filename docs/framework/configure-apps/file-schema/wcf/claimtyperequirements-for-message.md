---
title: '&lt;claimTypeRequirements&gt; de &lt;mensagem&gt;'
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: f4460311f5478f441b819bc8a48540d6feea69b1
ms.sourcegitcommit: 11f11ca6cefe555972b3a5c99729d1a7523d8f50
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/03/2018
---
# <a name="ltclaimtyperequirementsgt-for-ltmessagegt"></a>&lt;claimTypeRequirements&gt; de &lt;mensagem&gt;
Especifica uma coleção de tipos de declaração necessária.  
  
 A coleção é usada pelo serviço para especificar quaisquer declarações obrigatórias e opcionais que deverá ser o token emitido que o cliente usa para acessar o serviço. O serviço expõe os tipos de declaração necessária nos metadados se a publicação de WSDL está habilitada, mas WCF não exige que o token emitido contêm os tipos de declaração especificada. Serviços que deseja impor existem tipos de declaração necessária devem ser feito usando a política de autorização.  
  
 Em clientes federados, essa coleção contém a lista de declarações obrigatórias e opcionais que é enviada para o serviço de token de segurança na solicitação do cliente para um token emitido.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>  
 <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>  
 <xref:System.ServiceModel.Configuration.ClaimTypeElement>
