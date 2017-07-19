---
title: Instalar o .NET Framework 3.5 no Windows 10, Windows 8.1 e Windows 8 | Microsoft Docs
description: Saiba como instalar o .NET Framework 3.5 no Windows 10, no Windows 8.1 e no Windows 8
author: rlander
keywords: ".Net Framework, Instalação"
ms.date: 04/20/2017
ms.topic: article
ms.prod: .net-framework
ms.technology: vs-ide-deployment
ms.devlang: dotnet
ms.assetid: 67cda1d5-c6g4-4eb5-93e6-4f478de07ff7
ms.translationtype: Human Translation
ms.sourcegitcommit: 4437ce5d344cf06d30e31911def6287999fc6ffc
ms.openlocfilehash: 137436a073c050ed431b231204a3aca31c98c01a
ms.contentlocale: pt-br
ms.lasthandoff: 06/02/2017

---

# <a name="install-the-net-framework-35-on-windows-10-windows-81-and-windows-8"></a>Instalar o .NET Framework 3.5 no Windows 10, no Windows 8.1 e no Windows 8

Talvez você precise do .NET Framework 3.5 para executar um aplicativo no Windows 10, no Windows 8.1 e no Windows 8. Você também pode usar essas instruções para versões anteriores do Windows.

## <a name="install-the-net-framework-35-on-demand"></a>Instalação do .NET Framework 3.5 sob demanda

Se você tentar executar um aplicativo que exige o .NET Framework 3.5, você verá a seguinte caixa de diálogo de configuração. Escolha **Instalar este recurso** para habilitar o .NET Framework 3.5. Essa opção exige uma conexão com a Internet.

![Diálogo Instalação do .NET Framework](./media/dotnet-framework-installation-dialog.jpg)

## <a name="enable-the-net-framework-35-in-control-panel"></a>Habilitar o .NET Framework 3.5 no Painel de Controle

Você pode habilitar o .NET Framework 3.5 por meio do Painel de Controle do Windows. Essa opção exige uma conexão com a Internet.

1. Pressione a tecla Windows ![logotipo do Windows](https://i-msdn.sec.s-msft.com/dynimg/IC721376.jpeg) no teclado, digite “Recursos do Windows” e pressione Enter. A caixa de diálogo **Ativar ou desativar recursos do Windows** é exibida.

2. Marque a caixa de seleção **.NET Framework 3.5 (inclui o .NET 2.0 e 3.0)**, selecione OK e reinicialize o computador, se isso for solicitado.

   ![Instalar o .NET com o painel de controle](./media/dotnet-control-panel.png)

   Não é necessário selecionar os itens filho para a **Ativação HTTP do WCF (Windows Communication Foundation)** e para a **Ativação Não HTTP do WCF (Windows Communication Foundation)**, a menos que você seja um desenvolvedor ou administrador de servidor que exija essa funcionalidade.

