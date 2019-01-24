---
title: '&lt;claimTypeRequirements&gt; de &lt;mensagem&gt;'
ms.date: 03/30/2017
ms.assetid: f95c5ecd-abb6-4b77-a6d7-a38727f4a142
ms.openlocfilehash: 5c2bc05887701e78335629a37ce82815ac9abda5
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54628858"
---
# <a name="ltclaimtyperequirementsgt-for-ltmessagegt"></a>&lt;claimTypeRequirements&gt; de &lt;mensagem&gt;
Especifica uma coleção de tipos de declaração exigidos.  
  
 A coleção é usada pelo serviço para especificar quaisquer declarações obrigatórias e opcionais que devem ser no token emitido, que o cliente usa para acessar o serviço. O serviço expõe os tipos de declaração necessária nos metadados se a publicação de WSDL está habilitada, mas o WCF não exige o token emitido contêm os tipos de declaração especificado. Serviços que desejam impor declaração necessária tipos estão presentes devem fazer usando a política de autorização.  
  
 Em clientes federados, essa coleção contém a lista de declarações obrigatórias e opcionais que é enviada para o serviço de token de segurança na solicitação do cliente para um token emitido.  
  
## <a name="see-also"></a>Consulte também
- <xref:System.ServiceModel.FederatedMessageSecurityOverHttp.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Security.Tokens.ClaimTypeRequirement>
- <xref:System.ServiceModel.Configuration.FederatedMessageSecurityOverHttpElement.ClaimTypeRequirements%2A>
- <xref:System.ServiceModel.Configuration.ClaimTypeElementCollection>
- <xref:System.ServiceModel.Configuration.ClaimTypeElement>
