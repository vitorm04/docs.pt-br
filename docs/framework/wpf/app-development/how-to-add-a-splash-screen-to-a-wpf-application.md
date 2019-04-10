---
title: 'Como: Adicionar uma tela inicial a um aplicativo WPF'
ms.date: 08/18/2018
helpviewer_keywords:
- WPF [WPF], splash screen
- startup window [WPF]
- SplashScreen class [WPF]
- splash screen [WPF]
ms.assetid: d70a25c4-5fb9-4c27-b01d-b1b8ef39b3fd
ms.openlocfilehash: 3120ee64d65822d323800a89466c6b707169aaaa
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59307459"
---
# <a name="how-to-add-a-splash-screen-to-a-wpf-application"></a>Como: Adicionar uma tela inicial a um aplicativo WPF

Este tópico mostra como adicionar uma janela de inicialização ou *tela inicial*, para um aplicativo do Windows Presentation Foundation (WPF).

## <a name="to-add-an-existing-image-as-a-splash-screen"></a>Para adicionar uma imagem existente como uma tela inicial

1. Crie ou localize uma imagem que deseja usar para a tela inicial. Você pode usar qualquer formato de imagem com suporte do Windows Imaging Component (WIC). Por exemplo, você pode usar o formato TIFF, GIF, JPEG, PNG ou BMP.

2. Adicione o arquivo de imagem ao projeto de aplicativo do WPF.

3. Na **Gerenciador de soluções**, selecione a imagem.

4. Na janela Propriedades, clique na seta suspensa para a propriedade **Build Action**.

5. Selecione **SplashScreen** na lista suspensa.

6. Pressione **F5** para compilar e executar o aplicativo.

     A imagem da tela inicial aparece no centro da tela e, em seguida, desaparece quando a janela principal do aplicativo aparecer.

## <a name="to-exclude-the-splash-screen-from-build"></a>Para excluir a tela inicial de build

1. Na **Gerenciador de soluções**, selecione a imagem da tela inicial.

2. No **propriedades** janela, defina as **Build Action** para **None**.

## <a name="to-remove-the-splash-screen-from-an-application"></a>Para remover a tela inicial de um aplicativo

Na **Gerenciador de soluções**, exclua a imagem da tela inicial.

## <a name="see-also"></a>Consulte também

- <xref:System.Windows.SplashScreen>
- [Como: Adicionar itens existentes a um projeto](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/9f4t9t92(v=vs.100))
