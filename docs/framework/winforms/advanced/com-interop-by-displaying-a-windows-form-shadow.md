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
ms.openlocfilehash: 81220ad4c0bf00a38abfe7257d5fc61e92e8d885
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61779087"
---
# <a name="how-to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>Como: dar suporte à interoperabilidade COM exibindo um formulário do Windows com o método ShowDialog
Você pode resolver problemas de interoperabilidade do modelo de objeto de componente (COM) exibindo o formulário do Windows em um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] loop de mensagem, que é criado usando o <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> método.  
  
 Para fazer um formulário funcionar corretamente em um aplicativo cliente COM, você deve executá-lo em um loop de mensagem do Windows Forms. Para fazer isso, use uma das abordagens a seguir:  
  
- Use o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método para exibir o formulário do Windows;  
  
- Exiba cada Windows Form em um thread separado. Para obter mais informações, confira [Como: Dar suporte à interoperabilidade com exibindo cada formulário do Windows em seu próprio Thread](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md).  
  
## <a name="procedure"></a>Procedimento  
 Usando o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método pode ser a maneira mais fácil de exibir um formulário em um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] loop de mensagem porque, de todas as abordagens, ele requer o mínimo de código para implementar.  
  
 O <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método suspende o loop de mensagem do aplicativo não gerenciado e exibe o formulário como uma caixa de diálogo. Porque o loop de mensagem do aplicativo host foi suspenso, o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método cria um novo [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] loop de mensagem para processar mensagens do formulário.  
  
 A desvantagem de usar o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método é que o formulário será aberto como uma caixa de diálogo modal. Esse comportamento bloqueia qualquer interface do usuário (IU) do aplicativo de chamada enquanto o Windows Form está aberto. Quando o usuário sai do formulário, o loop de mensagem [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] fecha e o loop de mensagem do aplicativo anterior começa a ser executado novamente.  
  
 Você pode criar uma biblioteca de classes do Windows Forms que tem um método para mostrar o formulário e, em seguida, compilar a biblioteca de classes para interoperabilidade COM. Você pode usar este arquivo DLL do Visual Basic 6.0 ou o Microsoft Foundation Classes (MFC) e de qualquer um desses ambientes você pode chamar o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método para exibir o formulário.  
  
#### <a name="to-support-com-interop-by-displaying-a-windows-form-with-the-showdialog-method"></a>Dar suporte à interoperabilidade COM exibindo um formulário do Windows com o método ShowDialog  
  
- Substitua todas as chamadas para o <xref:System.Windows.Forms.Form.Show%2A?displayProperty=nameWithType> método com chamadas para o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método na sua [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] componente.  
  
## <a name="see-also"></a>Consulte também

- [Expondo componentes do .NET Framework ao COM](../../interop/exposing-dotnet-components-to-com.md)
- [Como: Dar suporte à interoperabilidade com exibindo cada formulário do Windows em seu próprio Thread](how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread.md)
- [Windows Forms e Aplicativos Não Gerenciados](windows-forms-and-unmanaged-applications.md)
