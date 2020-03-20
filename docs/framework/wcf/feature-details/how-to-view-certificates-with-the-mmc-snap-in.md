---
title: 'Como: Exibir certificados com o snap-in do MMC'
ms.date: 02/25/2019
helpviewer_keywords:
- certificates [WCF], viewing with the MMC snap-in
ms.assetid: 2b8782aa-ebb4-4ee7-974b-90299e356dc5
ms.openlocfilehash: 35048c24e838c513909fae8bedcba287001f5cef
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/12/2020
ms.locfileid: "79184778"
---
# <a name="how-to-view-certificates-with-the-mmc-snap-in"></a>Como: Exibir certificados com o snap-in do MMC
Quando você cria um cliente ou serviço seguro, você pode usar um [certificado](working-with-certificates.md) como credencial. Por exemplo, um tipo comum de credencial é o certificado X.509, que você cria com o <xref:System.ServiceModel.Security.X509CertificateInitiatorClientCredential.SetCertificate%2A?displayProperty=nameWithType> método.

Existem três tipos diferentes de lojas de certificados que você pode examinar com o Microsoft Management Console (MMC) em sistemas Windows:

- Computador local: A loja é local para o dispositivo e global para todos os usuários no dispositivo.

- Usuário atual: A loja é local para a conta de usuário atual no dispositivo.

- Conta de serviço: A loja é local para um determinado serviço no dispositivo.

## <a name="view-certificates-in-the-mmc-snap-in"></a>Exibir certificados no snap-in do MMC

O procedimento a seguir demonstra como examinar as lojas em seu dispositivo local para encontrar um certificado apropriado:
  
1. Selecione **Executar** no menu **Iniciar** e, em seguida, digite *mmc*.

    O MMC aparece.
  
2. No **menu Arquivo,** **selecione Adicionar/Remover encaixar**.

    A **janela Adicionar ou Remover Snap-ins** é exibida.
  
3. Na **lista de snap-ins disponíveis,** escolha **Certificados**e selecione **Adicionar**.  

    ![Adicionar snap-in de certificado](./media/mmc-add-certificate-snap-in.png)
  
4. Na janela **snap-in Certificados,** selecione **Conta de computador**e selecione **Next**.
  
    Opcionalmente, você pode selecionar **Minha conta de usuário** para a conta de usuário atual ou **serviço** para um determinado serviço.

    > [!NOTE]
    > Se você não é um administrador do seu dispositivo, você pode gerenciar certificados apenas para sua conta de usuário.
  
5. Na **janela Selecionar computador,** deixe o **computador local** selecionado e, em seguida, selecione **Concluir**.  
  
6. Na **janela Adicionar ou Remover snap-in,** selecione **OK**.  
  
    ![Adicionar snap-in de certificado](./media/mmc-certificate-snap-in-selected.png)

7. Opcional: No menu **Arquivo,** **selecione Salvar** ou **Salvar como** para salvar o arquivo do console MMC para uso posterior.  

8. Para exibir seus certificados no snap-in do MMC, selecione **'Raiz** de console' no painel esquerdo e expanda **Certificados (Computador Local)**.

    Uma lista de diretórios para cada tipo de certificado é exibida. A partir de cada diretório de certificados, você pode visualizar, exportar, importar e excluir seus certificados.

## <a name="view-certificates-with-the-certificate-manager-tool"></a>Exibir certificados com a ferramenta Gerenciador de certificados

Você também pode visualizar, exportar, importar e excluir certificados usando a ferramenta Gerenciador de certificados.

### <a name="to-view-certificates-for-the-local-device"></a>Para exibir certificados para o dispositivo local

1. Selecione **Executar** no menu **Iniciar** e, em seguida, *digite certlm.msc*.

    A ferramenta Gerenciador de certificados para o dispositivo local é exibida.
  
2. Para visualizar seus certificados, em **Certificados - Computador local** no painel esquerdo, expanda o diretório para o tipo de certificado que deseja exibir.

### <a name="to-view-certificates-for-the-current-user"></a>Para exibir certificados para o usuário atual

1. Selecione **Executar** no menu **Iniciar** e, em seguida, *digite certmgr.msc*.

    A ferramenta Gerenciador de certificados para o usuário atual é exibida.
  
2. Para visualizar seus certificados, em **Certificados - Usuário atual** no painel esquerdo, expanda o diretório para o tipo de certificado que deseja exibir.

## <a name="see-also"></a>Confira também

- [Trabalhando com certificados](working-with-certificates.md)
- [Como: Criar certificados temporários para uso durante o desenvolvimento](how-to-create-temporary-certificates-for-use-during-development.md)
- [Como: Recuperar a impressão digital de um certificado](how-to-retrieve-the-thumbprint-of-a-certificate.md)
