---
title: "Como especificar a cadeia de certificados da autoridade de certificação utilizada para verificar assinaturas (WCF)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f0ea15e8fe9580f561eedf048ed2aaf2e2ed248f
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Como especificar a cadeia de certificados da autoridade de certificação utilizada para verificar assinaturas (WCF)
Quando [!INCLUDE[indigo1](../../../../includes/indigo1-md.md)] recebe uma mensagem SOAP assinada usando um certificado x. 509, por padrão, ele verifica se o certificado x. 509 foi emitido por uma autoridade de certificação confiável. Isso é feito procurando em um repositório de certificados e determinar se o certificado de autoridade de certificação tiver sido designada como confiável. Para que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] para determinar isso, a cadeia de certificados de autoridade de certificação deve ser instalada no repositório de certificado correto.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Para instalar uma cadeia de certificados de autoridade de certificação  
  
-   Cada autoridade de certificação que pretenda confiar em certificados x. 509 emitido por um destinatário de mensagem SOAP, armazenar a cadeia de certificados de autoridade de certificação para o certificado de instalação que [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] está configurado para recuperar os certificados x. 509 De.  
  
     Por exemplo, se um destinatário da mensagem SOAP pretende confiar em certificados x. 509 emitidos pela Microsoft, a cadeia de certificados de autoridade de certificação para o Microsoft deve ser instalado no certificado do repositório de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] está configurado para procurar certificados x. 509 De. O repositório de certificados no qual [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] procura certificados x. 509 podem ser especificados no código ou configuração. Por exemplo, isso pode ser especificado no código usando o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> método ou na configuração de várias maneiras, incluindo o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Porque o Windows vem com um conjunto de cadeias de certificados padrão para autoridades de certificação confiáveis, não é necessário instalar a cadeia de certificados para todas as autoridades de certificação.  
  
    1.  Exporte a cadeia de certificados de autoridade de certificação.  
  
         Exatamente como fazer isso depende da autoridade de certificação. Se a autoridade de certificação estiver executando serviços de certificados Microsoft, selecione **baixar um certificado de autoridade de certificação, cadeia de certificados ou lista de certificados Revogados**e, em seguida, escolha **certificado de autoridade de certificação baixar**.  
  
    2.  Importe a cadeia de certificados de autoridade de certificação.  
  
         No Microsoft Management Console (MMC), abra o snap-in de certificados. Para o certificado do repositório de [!INCLUDE[indigo2](../../../../includes/indigo2-md.md)] está configurado para recuperar certificados x. 509, selecione o **raiz confiável** **autoridades de certificação**pasta. Sob o **autoridades de certificação raiz confiáveis** pasta, com o botão direito do **certificados**pasta, aponte para **todas as tarefas**e, em seguida, clique em **importação** . Forneça o arquivo exportado na etapa um.  
  
         [!INCLUDE[crabout](../../../../includes/crabout-md.md)]usando o snap-in de certificados com o MMC, consulte [como: exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
