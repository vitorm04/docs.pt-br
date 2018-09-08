---
title: Como recuperar a impressão digital de um certificado
ms.date: 03/30/2017
helpviewer_keywords:
- certificates [WCF], retrieving thumbprint
ms.assetid: da3101aa-78cd-4c34-9652-d1f24777eeab
ms.openlocfilehash: f520e897ad467686e0dc151548a61ea8370eb07a
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44133224"
---
# <a name="how-to-retrieve-the-thumbprint-of-a-certificate"></a>Como recuperar a impressão digital de um certificado
Ao escrever um aplicativo do Windows Communication Foundation (WCF) que usa um certificado X.509 para autenticação, muitas vezes é necessário especificar declarações encontrados no certificado. Por exemplo, você deve fornecer uma declaração de impressão digital ao usar o <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint> enumeração no <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A> método. Localizar o valor da declaração requer duas etapas. Primeiro, abra o snap-in do Console de gerenciamento Microsoft (MMC) para certificados. (Consulte [como: exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).) Segundo, conforme descrito aqui, localizar um certificado apropriado e copiar sua impressão digital (ou outros valores de declaração).  
  
 Se você estiver usando um certificado para autenticação de serviço, é importante observar o valor de **emitido para** coluna (a primeira coluna no console). Ao usar Secure Sockets Layer (SSL) como uma segurança de transporte, uma das verificações primeiro feitas é comparar a base de dados de endereços identificador de URI (Uniform Resource) de um serviço para o **emitido para** valor. Os valores devem coincidir ou o processo de autenticação é interrompido.  
  
 Você também pode usar o cmdlet New-SelfSignedCertificate do Powershell para criar certificados temporários para uso somente durante o desenvolvimento. Por padrão, no entanto, esse certificado não é emitido por uma autoridade de certificação e não pode ser usado para fins de produção. Para obter mais informações, consulte [como: criar certificados temporários para uso durante o desenvolvimento](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md).  
  
### <a name="to-retrieve-a-certificates-thumbprint"></a>Para recuperar uma impressão digital de certificado  
  
1.  Abra o snap-in do Console de gerenciamento Microsoft (MMC) para certificados. (Consulte [como: exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md).)  
  
2.  No **raiz do Console** janela esquerda do painel, clique em **certificados (computador Local)**.  
  
3.  Clique o **pessoais** para expandi-lo.  
  
4.  Clique o **certificados** para expandi-lo.  
  
5.  Na lista de certificados, observe os **finalidades pretendidas** título. Localizar um certificado que liste **autenticação de cliente** como uma finalidade pretendida.  
  
6.  Clique duas vezes no certificado.  
  
7.  No **certificado** caixa de diálogo, clique o **detalhes** guia.  
  
8.  Percorra a lista de campos e clique em **impressão digital**.  
  
9. Copie os caracteres hexadecimais de caixa. Se essa impressão digital é usada no código para o `X509FindType`, remova os espaços entre os números hexadecimais. Por exemplo, a impressão digital "a9 09 50 2d d8 2a e4 14 f8 de 33 e6 38 86 7b de 2a de a3 77 do b0 0d 42" deve ser especificado como "a909502dd82ae41433e6f83886b00d4277a32a7b" no código.  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Security.Cryptography.X509Certificates.X509FindType.FindByThumbprint>  
 <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>  
 [Como configurar uma porta com um certificado SSL](../../../../docs/framework/wcf/feature-details/how-to-configure-a-port-with-an-ssl-certificate.md)  
 [Como exibir certificados com o Snap-in do MMC](../../../../docs/framework/wcf/feature-details/how-to-view-certificates-with-the-mmc-snap-in.md)  
 [Como criar certificados temporários para uso durante o desenvolvimento](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)
