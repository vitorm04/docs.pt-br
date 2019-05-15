---
title: 'Como: dar suporte à interoperabilidade COM exibindo um formulário do Windows com o método ShowDialog'
ms.date: 03/30/2017
helpviewer_keywords:
- COM [Windows Forms]
- Windows Forms, unmanaged
- COM interop [Windows Forms], calling methods
- ActiveX controls [Windows Forms], COM interop
- Windows Forms, interop
ms.assetid: 87aac8ad-3c04-43b3-9b0c-d0b00df9ee74
ms.openlocfilehash: f2fb48e07243694b14904b240bdcb0739175c2fc
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/14/2019
ms.locfileid: "65593531"
---
# <a name="how-to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>Como: dar suporte à interoperabilidade COM exibindo um formulário do Windows com o método ShowDialog
Você pode resolver problemas de interoperabilidade do modelo de objeto de componente (COM) exibindo o formulário do Windows em um loop de mensagem do .NET Framework, que é criado usando o <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> método.  
  
 Para fazer um formulário funcionar corretamente em um aplicativo cliente COM, você deve executá-lo em um loop de mensagem do Windows Forms. Para fazer isso, use uma das abordagens a seguir:  
  
- Use o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método para exibir o formulário do Windows;  
  
- Exiba cada Windows Form em um thread separado. Para obter mais informações, confira [Como: Dar suporte à interoperabilidade com exibindo cada formulário do Windows em seu próprio Thread](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## <a name="procedure"></a>Procedimento  
 Usando o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método pode ser a maneira mais fácil para exibir um formulário em um loop de mensagem do .NET Framework porque, de todas as abordagens, ele requer o mínimo de código para implementar.  
  
 O <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método suspende o loop de mensagem do aplicativo não gerenciado e exibe o formulário como uma caixa de diálogo. Porque o loop de mensagem do aplicativo host foi suspenso, o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método cria um novo loop de mensagens do .NET Framework para processar mensagens do formulário.  
  
 A desvantagem de usar o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método é que o formulário será aberto como uma caixa de diálogo modal. Esse comportamento bloqueia qualquer interface do usuário (IU) do aplicativo de chamada enquanto o Windows Form está aberto. Quando o usuário sai do formulário, fecha o loop de mensagem do .NET Framework e o loop de mensagem do aplicativo anterior começa a ser executado novamente.  
  
 Você pode criar uma biblioteca de classes do Windows Forms que tem um método para mostrar o formulário e, em seguida, compilar a biblioteca de classes para interoperabilidade COM. Você pode usar este arquivo DLL do Visual Basic 6.0 ou o Microsoft Foundation Classes (MFC) e de qualquer um desses ambientes você pode chamar o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método para exibir o formulário.  
  
#### <a name="to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>Dar suporte à interoperabilidade COM exibindo um formulário do Windows com o método ShowDialog  
  
- Substitua todas as chamadas para o <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> método com chamadas para o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método no seu componente do .NET Framework.  
  
## <a name="see-also"></a>Consulte também

- [Expondo componentes do .NET Framework ao COM](../../interop/exposing-dotnet-components-to-com.md)
- [Como: Dar suporte à interoperabilidade com exibindo cada formulário do Windows em seu próprio Thread](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
- [Windows Forms e Aplicativos Não Gerenciados](windows-forms-and-unmanaged-applications.md)
