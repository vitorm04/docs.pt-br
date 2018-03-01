---
title: Como obter um certificado (WCF)
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], obtaining
ms.assetid: d53762fd-15ea-42dc-b0ea-6a6597aa23f7
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 5dcefa658aec37b9af3c4f9285ec76a0d549b868
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-obtain-a-certificate-wcf"></a>Como obter um certificado (WCF)
Usar o [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] recursos que usam certificados x. 509, apenas o primeiro obter certificados.  
  
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
