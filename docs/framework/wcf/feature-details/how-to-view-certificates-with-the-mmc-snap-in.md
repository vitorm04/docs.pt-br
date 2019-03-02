---
title: 'Como: Exibir certificados com o snap-in do MMC'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 6ec86ffca9ae84a9c3276a3dd6de676919dcd2e0
ms.sourcegitcommit: 41c0637e894fbcd0713d46d6ef1866f08dc321a2
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57200280"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Como: Exibir certificados com o snap-in do MMC
Quando você cria um cliente seguro ou serviço, você pode usar um [certificado](working-with-certificates.md) como a credencial. Por exemplo, um tipo comum de credencial é o certificado X.509, que você criar com o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> método. 

Há três tipos diferentes de repositórios de certificados que você pode examinar com o Microsoft Management Console (MMC) em sistemas Windows:

- Computador local: O armazenamento é global para todos os usuários no dispositivo e local para o dispositivo.

- Usuário atual: O armazenamento é local para a conta de usuário atual no dispositivo.

- Conta de serviço: O armazenamento é local para um serviço específico no dispositivo.

  
## <a name="view-certificates-in-the-mmc-snap-in"></a>Exibir certificados no snap-in do MMC 

O procedimento a seguir demonstra como examinar os repositórios em seu dispositivo local para localizar um certificado apropriado: 
  
1. Selecione **executados** da **inicie** menu e, em seguida, insira *mmc*. 

    O MMC é exibida. 
  
2. Dos **arquivo** menu, selecione **Adicionar/Remover Snap-In do**. 
    
    O **adicionar ou Remover Snap-ins** janela é exibida.
  
3. Dos **snap-ins disponíveis** , escolha **certificados**, em seguida, selecione **adicionar**.  

    ![Adicionar snap-in de certificado](./media/mmc-add-certificate-snap-in.png)
  
4. No **snap-in de certificados** janela, selecione **conta de computador**e, em seguida, selecione **próxima**. 
  
    Opcionalmente, você pode selecionar **minha conta de usuário** para o usuário atual ou **conta de serviço** para um serviço específico. 

    > [!NOTE]
    > Se você não for um administrador para seu dispositivo, você pode gerenciar certificados somente para sua conta de usuário.
  
5. No **Selecionar computador** janela, deixe **computador Local** selecionado e, em seguida, selecione **concluir**.  
  
6. No **adicionar ou Remover Snap-in** janela, selecione **Okey**.  
  
    ![Adicionar snap-in de certificado](./media/mmc-certificate-snap-in-selected.png)

7. Opcionais: Dos **arquivo** menu, selecione **salve** ou **Salvar como** para salvar o arquivo de console do MMC para uso posterior.  

8. Para exibir os certificados no snap-in do MMC, selecione **raiz do Console** no painel esquerdo, expanda **certificados (computador Local)**.

    É exibida uma lista de diretórios para cada tipo de certificado. Cada diretório de certificado, você pode exibir, exportar, importar e excluir seus certificados.
  

## <a name="view-certificates-with-the-certificate-manager-tool"></a>Exibir certificados com a ferramenta de Gerenciador de certificados

Você também pode exibir, exportar, importar e excluir certificados usando a ferramenta de Gerenciador de certificados.

### <a name="to-view-certificates-for-the-local-device"></a>Para exibir certificados para o dispositivo local

1. Selecione **executados** da **inicie** menu e, em seguida, insira *certlm*. 

    A ferramenta de Gerenciador de certificados para o dispositivo local é exibido. 
  
2. Para exibir os certificados, em **certificados - computador Local** no painel esquerdo, expanda o diretório para o tipo de certificado que você deseja exibir.

### <a name="to-view-certificates-for-the-current-user"></a>Para exibir certificados para o usuário atual

1. Selecione **executados** da **inicie** menu e, em seguida, insira *certmgr. msc*. 

    A ferramenta de Gerenciador de certificados para o usuário atual é exibida. 
  
2. Para exibir os certificados, em **certificados - usuário atual** no painel esquerdo, expanda o diretório para o tipo de certificado que você deseja exibir.

  
## <a name="see-also"></a>Consulte também
- [Trabalhando com certificados](working-with-certificates.md)
- [Como: Criar certificados temporários para uso durante o desenvolvimento](how-to-create-temporary-certificates-for-use-during-development.md)
- [Como: Recuperar a impressão digital de um certificado](how-to-retrieve-the-thumbprint-of-a-certificate.md)
