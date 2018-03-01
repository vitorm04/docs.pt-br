---
title: Como exibir certificados com o snap-in do MMC
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
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 582eaef518e10acb4c4c356226ce0be24d1b4c35
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Como exibir certificados com o snap-in do MMC
Um tipo comum de credenciais é o certificado X.509. Ao criar serviços ou clientes seguros, você poderá especificar que um certificado seja usado como a credencial de cliente ou serviço usando métodos como <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A>. O método exige vários parâmetros, como o armazenamento onde o certificado está armazenado e um valor para usar ao procurar pelo certificado. O procedimento a seguir demonstra como examinar os repositórios em um computador para localizar um certificado apropriado. Para obter um exemplo de encontrar a impressão digital do certificado, consulte [como: recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md).  
  
### <a name="to-view-certificates-in-the-mmc-snap-in"></a>Para exibir certificados no snap-in do MMC  
  
1.  Abra uma janela do Prompt de Comando.  
  
2.  Tipo `mmc` e pressione a tecla ENTER. Observe que, para exibir certificados no armazenamento do computador local, você deverá estar na função de Administrador.  
  
3.  Sobre o **arquivo** menu, clique em **Adicionar/Remover Snap-In do**.  
  
4.  Clique em **Adicionar**.  
  
5.  No **Adicionar Snap-in Standalone** caixa de diálogo, selecione **certificados**.  
  
6.  Clique em **Adicionar**.  
  
7.  No **snap-in de certificados** caixa de diálogo, selecione **conta de computador** e clique em **próximo**. Opcionalmente, você pode selecionar **conta de usuário Meus** ou **conta de serviço**. Se você não for administrador do computador, pode gerenciar certificados somente para sua conta de usuário.  
  
8.  No **Selecionar computador** caixa de diálogo, clique em **concluir**.  
  
9. No **Adicionar Snap-in Standalone** caixa de diálogo, clique em **fechar**.  
  
10. Sobre o **Adicionar/Remover Snap-in** caixa de diálogo, clique em **Okey**.  
  
11. No **raiz do Console** janela, clique em **certificados (computador Local)** para exibir o certificado armazena para o computador.  
  
12. Opcional. Para exibir certificados para sua conta, repita as etapas de 3 a 6. Na etapa 7, em vez de selecionar **conta de computador**, clique em **conta de usuário Meus** e repita as etapas 8 a 10.  
  
13. Opcional. Sobre o **arquivo** menu, clique em **salvar** ou **Salvar como**. Salve o arquivo de console para reutilização posterior.  
  
## <a name="viewing-certificates-with-internet-explorer"></a>Exibindo certificados com o Internet Explorer  
 Você também pode exibir, exportar, importar e excluir certificados usando o Internet Explorer.  
  
#### <a name="to-view-certificates-with-internet-explorer"></a>Para exibir certificados com o Internet Explorer  
  
1.  No Internet Explorer, clique em **ferramentas**, em seguida, clique em **opções da Internet** para exibir o **opções da Internet** caixa de diálogo.  
  
2.  Clique o **conteúdo** guia.  
  
3.  Em **certificados**, clique em **certificados**.  
  
4.  Para exibir detalhes de qualquer certificado, selecione o certificado e clique em **exibição**.  
  
## <a name="see-also"></a>Consulte também  
 [Trabalhando com certificados](../../../../docs/framework/wcf/feature-details/working-with-certificates.md)  
 [Como criar certificados temporários para uso durante o desenvolvimento](../../../../docs/framework/wcf/feature-details/how-to-create-temporary-certificates-for-use-during-development.md)  
 [Como recuperar a impressão digital de um certificado](../../../../docs/framework/wcf/feature-details/how-to-retrieve-the-thumbprint-of-a-certificate.md)
