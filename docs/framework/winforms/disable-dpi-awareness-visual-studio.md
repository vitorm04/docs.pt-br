---
title: Desabilitar o reconhecimento de DPI no Visual Studio
description: Discute as limitações do Designer de formulários do Windows em monitores HDPI e como executar o Visual Studio como um processo sem reconhecimento de DPI.
ms.date: 08/14/2018
ms.prod: visual-studio-dev15
ms.technology: vs-ide-designers
author: gewarren
ms.author: gewarren
ms.openlocfilehash: 2d3466476c33a3e5faa8be96d63f1d11442c5d70
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 12/10/2018
ms.locfileid: "53151259"
---
# <a name="disable-dpi-awareness-in-visual-studio"></a>Desabilitar o reconhecimento de DPI no Visual Studio

O Visual Studio é um pontos por polegada (DPI) com suporte a aplicativo, o que significa que as escalas de exibição automaticamente. Se um aplicativo declara que ele não é com reconhecimento de DPI, o sistema operacional dimensiona o aplicativo como um bitmap. Esse comportamento também é chamado de virtualização de DPI. O aplicativo ainda acha que está executando em escala de 100% ou 96 dpi.

## <a name="windows-forms-designer-on-hdpi-monitors"></a>Designer de formulários do Windows em monitores HDPI

O **Designer de formulários do Windows** no Visual Studio não tem suporte a dimensionamento. Isso causa problemas de exibição quando você abrir alguns formulários na **Designer de formulários do Windows** em alta pontos por polegada (HDPI) monitores. Para obter exemplos, os controles podem aparecer sobrepor conforme mostrado na imagem a seguir:

![Designer de formulários do Windows no monitor HDPI](media/disable-dpi-awareness-visual-studio/win-forms-designer-hdpi.png)

No Visual Studio 2017 versão 15,8 e posterior, quando você abre um formulário na **Designer de formulários do Windows** em um monitor HDPI, o Visual Studio exibe uma amarela informativa barra na parte superior do designer:

![Barra informativa no Visual Studio para reiniciar no modo de reconhecimento de DPI](media/disable-dpi-awareness-visual-studio/scaling-gold-bar.png)

Lê a mensagem **colocação em escala no vídeo principal está definida para 200% (192 dpi). Isso pode causar problemas de renderização na janela do designer.**

Se você não estiver trabalhando no designer e não é necessário ajustar o layout do formulário, você pode ignorar a barra informativa e continuar trabalhando no editor de código ou em outros tipos de designers. Somente o **Designer de formulários do Windows** é afetado. Se você precisar trabalhar **Designer de formulários do Windows**, a próxima seção ajuda você [resolver o problema](#to-resolve-the-problem).

## <a name="to-resolve-the-problem"></a>Para resolver o problema

Há três opções para resolver o problema de exibição.

### <a name="restart-visual-studio-as-a-dpi-unaware-process"></a>Reinicie o Visual Studio como um processo sem reconhecimento de DPI

Você pode reiniciar o Visual Studio como um processo sem reconhecimento de DPI, selecionando a opção na barra informativa amarela. Isso é a melhor maneira de resolver o problema.

Quando o Visual Studio é executado como um processo sem reconhecimento de DPI, os problemas de layout do designer são resolvidos, mas fontes podem aparecer desfocadas. Visual Studio exibe uma mensagem de informação amarela diferente quando ele é executado como um processo sem reconhecimento de DPI que diz **Visual Studio está em execução como um processo sem reconhecimento de DPI. WPF e XAML designers poderão não ser exibidos corretamente.** Barra informativa também fornece uma opção para **reinicie o Visual Studio como um processo de reconhecimento de DPI**.

> [!NOTE]
> - Se você tivesse desencaixado janelas de ferramenta no Visual Studio quando você tiver selecionado a opção de reiniciar como um processo sem reconhecimento de DPI, pode alterar a posição dessas janelas de ferramenta.
> - Se você usar o perfil padrão do Visual Basic, ou se você tiver o **salvar novos projetos quando criados** opção desmarcada na **ferramentas** > **opções**  >  **Projetos e soluções**, Visual Studio não é possível reabrir o projeto quando ele for reiniciado como um processo sem reconhecimento de DPI. No entanto, você pode abrir o projeto, selecionando-o sob **arquivo** > **projetos e soluções recentes**.

É importante reiniciar o Visual Studio como um processo de reconhecimento de DPI quando tiver terminado de trabalhar na **Designer de formulários do Windows**. Quando ele é executado como um processo sem reconhecimento de DPI, fontes podem parecerem desfocadas e talvez você veja problemas em outros designers, como o **XAML Designer**. Se você fechar e reabrir o Visual Studio quando ele está em execução no modo de reconhecimento de DPI, torna-se com reconhecimento de DPI novamente. Você também pode clicar na **reinicie o Visual Studio como um processo de reconhecimento de DPI** opção na barra informativa.

### <a name="add-a-registry-entry"></a>Adicionar uma entrada de registro

Você pode marcar o Visual Studio como reconhecimento de DPI modificando o registro. Abra **Editor do registro** e adicione uma entrada para o **NT\CurrentVersion\AppCompatFlags\Layers HKEY_CURRENT_USER\SOFTWARE\Microsoft\Windows** subchave:

**Entrada**: C:\Program arquivos (x86) \Microsoft Visual Studio\2017\Community\Common7\IDE\devenv.exe

   > [!NOTE]
   > Se você estiver usando a edição Professional ou Enterprise do Visual Studio 2017, substitua **Community** com **Professional** ou **Enterprise** na entrada. Também, substitua a letra da unidade conforme necessário.

**Tipo**: REG_SZ

**Valor**: DPIUNAWARE

> [!NOTE]
> Visual Studio permanece no modo de reconhecimento de DPI até que você remova a entrada do registro.

### <a name="set-your-display-scaling-setting-to-100"></a>Definir seu dimensionamento de configuração para 100% da exibição

Para definir seu dimensionamento de configuração para 100% no Windows 10 da exibição, digite **configurações de exibição** na barra da caixa de pesquisa e, em seguida, selecione de tarefas **alterar configurações de exibição**. No **as configurações** janela, defina **alterar o tamanho do texto, aplicativos e outros itens** para **100%**.

Definir seu dimensionamento para 100% da exibição pode ser indesejável, pois isso pode tornar a interface do usuário muito pequeno para ser usado.

## <a name="troubleshoot"></a>Solução de problemas

Se a transição de reconhecimento de DPI não está funcionando conforme o esperado no Visual Studio, verifique se você tem o `dpiAwareness` o valor de **HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows NT\CurrentVersion\Image arquivo execução Options\devenv.exe**  subchave no Editor do registro. Exclua o valor se ele estiver presente.

## <a name="see-also"></a>Consulte também

- [Dimensionamento automático no Windows Forms](automatic-scaling-in-windows-forms.md)
