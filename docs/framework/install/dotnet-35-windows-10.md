---
title: Instalar o .NET Framework 3.5 no Windows 10, no Windows 8.1 e no Windows 8
description: Saiba como instalar o .NET Framework 3.5 no Windows 10, no Windows 8.1 e no Windows 8.
author: rlander
ms.author: mairaw
ms.date: 11/27/2017
ms.topic: article
ms.prod: .net-framework
ms.workload:
- dotnet
ms.openlocfilehash: e81008eca3019860789db548d40998a7a7565d31
ms.sourcegitcommit: cec0525b2121c36198379525e69aa5388266db5b
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 02/23/2018
---
# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Instalar o .NET Framework 3.5 no Windows 10, no Windows 8.1 e no Windows 8

Talvez você precise do .NET Framework 3.5 para executar um aplicativo no Windows 10, no Windows 8.1 e no Windows 8. Você também pode usar essas instruções para versões anteriores do Windows.

## <a name="install-the-net-framework-35-on-demand"></a>Instalação do .NET Framework 3.5 sob demanda

Se você tentar executar um aplicativo que exige o .NET Framework 3.5, você verá a seguinte caixa de diálogo de configuração. Escolha **Instalar este recurso** para habilitar o .NET Framework 3.5. Essa opção exige uma conexão com a Internet.

![Diálogo Instalação do .NET Framework](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a>Habilitar o .NET Framework 3.5 no Painel de Controle

Você pode habilitar o .NET Framework 3.5 por meio do Painel de Controle do Windows. Essa opção exige uma conexão com a Internet.

1. Pressione a tecla Windows ![logotipo do Windows](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) no teclado, digite “Recursos do Windows” e pressione Enter. A caixa de diálogo **Ativar ou desativar recursos do Windows** é exibida.

2. Marque a caixa de seleção **.NET Framework 3.5 (inclui o .NET 2.0 e 3.0)**, selecione **OK** e reinicialize o computador, se isso for solicitado.

   ![Instalar o .NET com o painel de controle](./media/dotnet-control-panel.png)

   Não é necessário selecionar os itens filho para a **Ativação HTTP do WCF (Windows Communication Foundation)** e para a **Ativação Não HTTP do WCF (Windows Communication Foundation)**, a menos que você seja um desenvolvedor ou administrador de servidor que exija essa funcionalidade.

## <a name="troubleshoot-the-installation-of-the-net-framework-35"></a>Solucionar problemas de instalação do .NET Framework 3.5

Durante a instalação, você poderá se deparar com o erro 0x800f0906, 0x800f0907, 0x800f081f ou 0x800F0922. Nesse caso, consulte [Erro de instalação do .NET Framework 3.5: 0x800f0906, 0x800f0907 ou 0x800f081f](https://support.microsoft.com/help/2734782/net-framework-3-5-installation-error-0x800f0906--0x800f081f--0x800f09) para descobrir como resolver esses problemas.

Se algum dos métodos discutidos no artigo anterior falhar ou se você não tiver uma conexão com a Internet, use a mídia de instalação do Windows. Para obter mais informações, consulte [Deploy .NET Framework 3.5 by using Deployment Image Servicing and Management (DISM)](/windows-hardware/manufacture/desktop/deploy-net-framework-35-by-using-deployment-image-servicing-and-management--dism) (Implantar o .NET Framework 3.5 usando o DISM (Gerenciamento e Manutenção de Imagens de Implantação)). Se você não tiver a mídia de instalação, confira [Criar mídia de instalação para Windows](https://support.microsoft.com/help/15088/windows-create-installation-media).
