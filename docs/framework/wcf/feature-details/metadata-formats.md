---
title: Formatos de metadados
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: a3c6b1f551d1bff8c68a91f33e62df289d2078cc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33493432"
---
# <a name="metadata-formats"></a>Formatos de metadados
Windows Communication Foundation (WCF) oferece suporte os formatos de metadados na tabela a seguir.  
  
## <a name="metadata-specifications-and-usage"></a>Especificações de metadados e de uso  
  
|Protocolo|Especificação e uso|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web Services Description Language (WSDL) 1.1](http://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> WCF usa WSDL Web Services Description Language () para descrever serviços.|  
|esquema XML|[Esquema XML parte 2: Edição de segundo de tipos de dados](http://go.microsoft.com/fwlink/?LinkId=94861) e [esquema XML parte 1: estruturas segunda edição](http://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> WCF usa o esquema XML para descrever tipos de dados usados em mensagens.|  
|Política de WS|[Política de serviços Web 1.2 - Framework (WS-Policy)](http://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [Política de serviços Web 1.5 - estrutura](http://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> WCF usa o WS-Policy 1.2 ou 1,5 especificações com declarações específicas de domínio para descrever os recursos e requisitos de serviço.|  
|Anexos de política WS|[Política de serviços Web 1.2 - anexo (mecanismo WS-PolicyAttachment)](http://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> O WCF implementa o WS-Policy anexos para anexar a expressões de política em vários escopos em WSDL.|  
|Troca de metadados de WS|[Troca de metadados de serviços da Web (WS-MetadataExchange) versão 1.1](http://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> O WCF implementa o WS-MetadataExchange para recuperar o esquema XML, WSDL e WS-Policy.|  
|WS endereçamento de associação para WSDL|[Associação de WSDL 1.0 - endereçamento de serviços Web](http://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> O WCF implementa o WS-Addressing associação WSDL anexar informações de endereçamento em WSDL.|  
  
## <a name="see-also"></a>Consulte também  
 [Protocolos de serviços Web com suporte em associações de interoperabilidade fornecidas pelo sistema](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)  
 [WSDL e política](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
