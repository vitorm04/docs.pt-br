---
title: 'Como: dar suporte à interoperabilidade COM exibindo cada formulário do Windows Forms em um thread separado'
ms.date: 03/30/2017
dev_langs:
- vb
helpviewer_keywords:
- COM interop [Windows Forms], Windows Forms
- COM [Windows Forms]
- Windows Forms, unmanaged
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: a9e04765-d2de-4389-a494-a9a6d07aa6ee
ms.openlocfilehash: 41af4d81995a0a4eac912ecce7dc70cf04f012cd
ms.sourcegitcommit: 1e72e2990220b3635cebc39586828af9deb72d8c
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/26/2019
ms.locfileid: "71306386"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>Como: Suporte à interoperabilidade COM exibindo cada formulário do Windows em seu próprio thread

Você pode resolver problemas de interoperabilidade com exibindo seu formulário em um .NET Framework loop de mensagem, que pode ser criado <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> usando o método.

Para fazer um Windows Form funcionar corretamente em um aplicativo cliente COM, execute o formulário em um loop de mensagem dos Windows Forms. Para fazer isso, use uma das abordagens a seguir:

- Use o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método para exibir o formulário do Windows. Para obter mais informações, confira [Como: Suporte à interoperabilidade COM exibindo um formulário do Windows](com-interop-by-displaying-a-windows-form-shadow.md)com o método ShowDialog.

- Exiba cada Windows Form em um thread separado.

Há amplo suporte para esse recurso no Visual Studio.

Consulte [também o passo a passos: Suporte à interoperabilidade COM exibindo cada formulário do Windows](https://docs.microsoft.com/previous-versions/visualstudio/visual-studio-2010/ms233639(v=vs.100))em seu próprio thread.

## <a name="example"></a>Exemplo

O exemplo de código a seguir demonstra como exibir o formulário em um thread separado e chamar <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> o método para iniciar um Windows Forms bomba de mensagem nesse thread. Para usar essa abordagem, você deve realizar marshaling de todas as chamadas para o formulário a partir do aplicativo não <xref:System.Windows.Forms.Control.Invoke%2A> gerenciado usando o método.

Essa abordagem requer que cada instância de um formulário seja executada em seu próprio thread usando seu próprio loop de mensagem. Não é possível ter mais de um loop de mensagem em execução por thread. Portanto, não é possível alterar o loop de mensagem do aplicativo cliente. No entanto, você pode modificar o componente .NET Framework para iniciar um novo thread que usa seu próprio loop de mensagem.

[!code-vb[System.Windows.Forms.ComInterop#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]

[!code-vb[System.Windows.Forms.ComInterop#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]

[!code-vb[System.Windows.Forms.ComInterop#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]

## <a name="compile-the-code"></a>Compilar o código

Compile os tipos `COMForm`, `Form1` e `FormManager` em um assembly chamado `COMWinform.dll`. Registre o assembly de interoperabilidade COM usando um dos métodos descritos em [Empacotando um assembly para COM](../../interop/packaging-an-assembly-for-com.md). Agora você pode usar o assembly e o arquivo de biblioteca de tipos (.tlb) correspondente em aplicativos não gerenciados. Por exemplo, você pode usar a biblioteca de tipos como uma referência em um projeto executável do Visual Basic 6.0.

## <a name="see-also"></a>Consulte também

- [Expondo componentes do .NET Framework ao COM](../../interop/exposing-dotnet-components-to-com.md)
- [Empacotando um assembly para COM](../../interop/packaging-an-assembly-for-com.md)
- [Registrando assemblies usando COM](../../interop/registering-assemblies-with-com.md)
- [Como: Suporte à interoperabilidade COM exibindo um formulário do Windows com o método ShowDialog](com-interop-by-displaying-a-windows-form-shadow.md)
- [Visão Geral dos Aplicativos dos Windows Forms e Aplicativos Não Gerenciados](windows-forms-and-unmanaged-applications-overview.md)
