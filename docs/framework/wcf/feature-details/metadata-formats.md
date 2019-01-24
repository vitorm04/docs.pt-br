---
title: Formatos de metadados
ms.date: 03/30/2017
ms.assetid: baad1e68-28fc-4a6a-8a43-75e47e7fa871
ms.openlocfilehash: 44ea084287561e13a8db217e49212ee878a26bb7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/23/2019
ms.locfileid: "54513511"
---
# <a name="metadata-formats"></a>Formatos de metadados
Windows Communication Foundation (WCF) oferece suporte os formatos de metadados na tabela a seguir.  
  
## <a name="metadata-specifications-and-usage"></a>Uso e especificações de metadados  
  
|Protocolo|Especificação e uso|  
|--------------|-----------------------------|  
|WSDL 1.1|[Web Services Description Language (WSDL) 1.1](https://go.microsoft.com/fwlink/?LinkId=94859)<br /><br /> Para descrever serviços, o WCF usa descrição linguagem WSDL (Web Services).|  
|esquema XML|[XML Schema Part 2: Datatypes Second Edition](https://go.microsoft.com/fwlink/?LinkId=94861) e [esquema XML parte 1: Segunda edição das estruturas](https://go.microsoft.com/fwlink/?LinkId=94862)<br /><br /> O WCF usa o esquema XML para descrever tipos de dados usados em mensagens.|  
|Política de WS|[Política de serviços Web 1.2 - Framework (WS-Policy)](https://go.microsoft.com/fwlink/?LinkId=94864)<br /><br /> [Política de serviços Web 1.5 - estrutura](https://go.microsoft.com/fwlink/?LinkId=94865)<br /><br /> WCF usa o WS-Policy 1.2 ou 1,5 especificações com declarações específicas de domínio para descrever os recursos e requisitos de serviço.|  
|Anexos da política WS|[Política de serviços Web 1.2 - anexo (mecanismo WS-PolicyAttachment)](https://go.microsoft.com/fwlink/?LinkId=94866)<br /><br /> O WCF implementa anexos de WS-Policy para anexar as expressões de diretriz em vários escopos em WSDL.|  
|Troca de metadados de WS|[Troca de metadados de serviços da Web (WS-MetadataExchange) versão 1.1](https://go.microsoft.com/fwlink/?LinkId=94868)<br /><br /> O WCF implementa o WS-MetadataExchange para recuperar o esquema XML, WSDL e WS-Policy.|  
|Endereçamento de associação para WSDL de WS|[Associação de WSDL 1.0 - endereçamento de serviços da Web](https://go.microsoft.com/fwlink/?LinkId=94869)<br /><br /> O WCF implementa o WS-Addressing de associação para o WSDL anexar informações de endereçamento no WSDL.|  
  
## <a name="see-also"></a>Consulte também
- [Protocolos de serviços Web com suporte em associações de interoperabilidade fornecidas pelo sistema](../../../../docs/framework/wcf/feature-details/web-services-protocols-supported-by-system-provided-interoperability-bindings.md)
- [WSDL e política](../../../../docs/framework/wcf/feature-details/wsdl-and-policy.md)
