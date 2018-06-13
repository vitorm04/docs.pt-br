---
title: Como dar suporte à interoperabilidade COM exibindo cada formulário do Windows Forms em um thread separado
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
ms.openlocfilehash: c78bcc8d784fc481af2449f2d81cfde42891e7fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522883"
---
# <a name="how-to-support-com-interop-by-displaying-each-windows-form-on-its-own-thread"></a>Como dar suporte à interoperabilidade COM exibindo cada formulário do Windows Forms em um thread separado
Você pode resolver problemas de interoperabilidade COM exibindo o formulário em um [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] loop de mensagem, você pode criar usando o <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> método.  
  
 Para fazer um Windows Form funcionar corretamente em um aplicativo cliente COM, execute o formulário em um loop de mensagem dos Windows Forms. Para fazer isso, use uma das abordagens a seguir:  
  
-   Use o <xref:System.Windows.Forms.Form.ShowDialog%2A?displayProperty=nameWithType> método para exibir o formulário do Windows. Para mais informações, consulte [Como dar suporte à interoperabilidade COM exibindo um Formulário do Windows Forms com o método ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md).  
  
-   Exiba cada Windows Form em um thread separado.  
  
 Há suporte abrangente para este recurso no Visual Studio.  
  
 Consulte também [Instruções passo a passo: dando suporte à interoperabilidade COM exibindo cada Windows Form no próprio thread](http://msdn.microsoft.com/library/ms233639\(v=vs.110\)).  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como exibir o formulário em um segmento separado e chamar o <xref:System.Windows.Forms.Application.Run%2A?displayProperty=nameWithType> método para iniciar uma bomba de mensagem de formulários do Windows naquele thread. Para usar essa abordagem, você deve empacotar as chamadas para o formulário do aplicativo não gerenciado usando o <xref:System.Windows.Forms.Control.Invoke%2A> método.  
  
 Essa abordagem requer que cada instância de um formulário seja executada em seu próprio thread usando seu próprio loop de mensagem. Não é possível ter mais de um loop de mensagem em execução por thread. Portanto, não é possível alterar o loop de mensagem do aplicativo cliente. No entanto, é possível modificar o componente [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] para iniciar um novo thread que usa seu próprio loop de mensagem.  
  
 [!code-vb[System.Windows.Forms.ComInterop#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/COMForm.vb#1)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#10](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/FormManager.vb#10)]  
  
 [!code-vb[System.Windows.Forms.ComInterop#100](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.ComInterop/VB/Form1.vb#100)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
  
-   Compile os tipos `COMForm`, `Form1` e `FormManager` em um assembly chamado `COMWinform.dll`. Registre o assembly de interoperabilidade COM usando um dos métodos descritos em [Empacotando um assembly para COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md). Agora você pode usar o assembly e o arquivo de biblioteca de tipos (.tlb) correspondente em aplicativos não gerenciados. Por exemplo, você pode usar a biblioteca de tipos como uma referência em um projeto executável do Visual Basic 6.0.  
  
## <a name="see-also"></a>Consulte também  
 [Expondo componentes do .NET Framework ao COM](../../../../docs/framework/interop/exposing-dotnet-components-to-com.md)  
 [Empacotando um assembly para COM](../../../../docs/framework/interop/packaging-an-assembly-for-com.md)  
 [Registrando assemblies usando COM](../../../../docs/framework/interop/registering-assemblies-with-com.md)  
 [Como dar suporte à interoperabilidade COM exibindo um Windows Form com o método ShowDialog](../../../../docs/framework/winforms/advanced/com-interop-by-displaying-a-windows-form-shadow.md)  
 [Visão Geral dos Aplicativos dos Windows Forms e Aplicativos Não Gerenciados](../../../../docs/framework/winforms/advanced/windows-forms-and-unmanaged-applications-overview.md)
