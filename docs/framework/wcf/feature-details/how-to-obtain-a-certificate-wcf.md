---
title: Como obter um certificado (WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
ms.openlocfilehash: 368401d91aa2a83110631d583660d6ccebf8d4fc
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33491501"
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Como obter um certificado (WCF)
Para usar qualquer do Windows Communication Foundation (WCF) recursos que usam certificados x. 509, apenas o primeiro obter certificados.  
  
### <a name="to-obtain-an-x509-certificate"></a>Para obter um certificado x. 509  
  
1.  Escolha uma das seguintes opções:  
  
    -   Compre um certificado de uma autoridade de certificação, como VeriSign, Inc.  
  
    -   Configurar seu próprio serviço de certificado e ter uma autoridade de certificação assinar os certificados. [!INCLUDE[ws2003](../../../../includes/ws2003-md.md)], Windows 2000 Server, o Windows 2000 Server Datacenter e o Windows 2000 Datacenter Server incluem os serviços de certificados que oferecem suporte à infraestrutura de chave pública (PKI). No Windows Server 2008, use o [serviços de certificados do Active Directory](http://go.microsoft.com/fwlink/?LinkID=153483) função para gerenciar uma autoridade de certificação.  
  
    -   Configurar seu próprio serviço de certificado e fazer não tem certificados assinados.  
  
    > [!NOTE]
    >  Qualquer abordagem, o destinatário da solicitação SOAP que contém o certificado x. 509 deve confiar no certificado de x. 509. Isso significa que o certificado x. 509 ou um emissor da cadeia de certificados no repositório de certificados de pessoas confiáveis e que o certificado x. 509 não está no repositório de certificados não confiáveis.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Como criar certificados temporários para uso durante o desenvolvimento](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
