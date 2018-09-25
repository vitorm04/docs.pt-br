---
title: Como especificar a cadeia de certificados da autoridade de certificação utilizada para verificar assinaturas (WCF)
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], specifying the certificate authority certificate chain
- certificates [WCF], verifying signatures
ms.assetid: 7c719355-aa41-4567-80d0-5115a8cf73fd
ms.openlocfilehash: 9e2ba9f3550442602cab217fec329e6c19efd3b3
ms.sourcegitcommit: 213292dfbb0c37d83f62709959ff55c50af5560d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/25/2018
ms.locfileid: "47080819"
---
# <a name="how-to-specify-the-certificate-authority-certificate-chain-used-to-verify-signatures-wcf"></a>Como especificar a cadeia de certificados da autoridade de certificação utilizada para verificar assinaturas (WCF)
Quando o Windows Communication Foundation (WCF) recebe uma mensagem SOAP assinada usando um certificado X.509, por padrão ele verifica se o certificado x. 509 foi emitido por uma autoridade de certificação confiável. Isso é feito procurando em um repositório de certificados e determinar se o certificado de autoridade de certificação tiver sido designada como confiável. Em ordem para o WCF tomar essa decisão, a cadeia de certificados de autoridade de certificação deve ser instalada no repositório de certificados correto.  
  
### <a name="to-install-a-certification-authority-certificate-chain"></a>Para instalar uma cadeia de certificados de autoridade de certificação  
  
-   Para cada autoridade de certificação que um destinatário de mensagem SOAP deve confiar em certificados x. 509 emitidos, instale a cadeia de certificados de autoridade de certificação no repositório de certificados que o WCF está configurado para recuperar os certificados x. 509 do.  
  
     Por exemplo, se um destinatário de mensagem SOAP pretende confiar em certificados x. 509 emitidos pela Microsoft, a cadeia de certificados de autoridade de certificação da Microsoft deve ser instalada no repositório de certificados que o WCF é configurado para procurar por certificados X.509 de. O repositório de certificados em que o WCF procura certificados x. 509 pode ser especificado no código ou configuração. Por exemplo, isso pode ser especificado no código usando o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> método ou na configuração de várias maneiras, incluindo o [ \<serviceCertificate >](../../../../docs/framework/configure-apps/file-schema/wcf/servicecertificate-of-clientcredentials-element.md) .  
  
     Porque o Windows é fornecido com um conjunto padrão de cadeias de certificados de autoridades de certificação confiáveis, não pode ser necessário instalar a cadeia de certificados para todas as autoridades de certificação.  
  
    1.  Exporte a cadeia de certificados de autoridade de certificação.  
  
         Exatamente como isso é feito depende da autoridade de certificação. Se a autoridade de certificação estiver executando serviços de certificados Microsoft, selecione **baixar um certificado de autoridade de certificação, cadeia de certificados ou lista de certificados Revogados**e, em seguida, escolha **certificado de autoridade de certificação baixar**.  
  
    2.  Importe a cadeia de certificados de autoridade de certificação.  
  
         No Microsoft Management Console (MMC), abra o snap-in de certificados. Para o repositório de certificados que o WCF é configurado para recuperar certificados x. 509 no, selecione a **raiz confiáveis** **autoridades de certificação** pasta. Sob o **autoridades de certificação raiz confiáveis** pasta, com o botão direito do **certificados** pasta, aponte para **todas as tarefas**e, em seguida, clique em **importação** . Forneça o arquivo exportado na etapa um.  
  
         Para obter mais informações sobre como usar o snap-in de certificados com o MMC, consulte [como: exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)
