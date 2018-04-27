---
title: Como adicionar recursos do navegador da Web a um Aplicativo do Windows Forms
ms.custom: ''
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: ''
ms.suite: ''
ms.technology:
- dotnet-winforms
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- WebBrowser control [Windows Forms], adding Web browser capabilities to your application
- WebBrowser control [Windows Forms], examples
- Web browsers [.NET Framework], adding to Windows Forms
- examples [Windows Forms], WebBrowser control
- Windows Forms, adding Web browser functionality
ms.assetid: 3871f072-b57a-435b-9976-e5da28df04a7
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 3e7cde23c7395e778f8f6cf9b13f998dded18d69
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-add-web-browser-capabilities-to-a-windows-forms-application"></a>Como adicionar recursos do navegador da Web a um Aplicativo do Windows Forms
Com o <xref:System.Windows.Forms.WebBrowser> controle, você pode adicionar funcionalidade do navegador da Web para seu aplicativo. O controle funciona como um navegador da Web por padrão. Depois que você carregar uma URL inicial, definindo o <xref:System.Windows.Forms.WebBrowser.Url%2A> propriedade, você pode navegar clicando em hiperlinks ou usando atalhos de teclado para retroceder e Avançar no histórico de navegação. Por padrão, você pode acessar a funcionalidade adicional do navegador por meio do menu de atalho acessado quando se clica com o botão direito do mouse. Você também pode abrir novos documentos soltando-os no controle. O <xref:System.Windows.Forms.WebBrowser> controle também tem várias propriedades, métodos e eventos que você pode usar para implementar recursos de interface de usuário semelhantes àqueles encontrados no Internet Explorer.  
  
 O exemplo de código a seguir implementa uma barra de endereços, botões de navegador típicos, um menu **Arquivo**, uma barra de status e uma barra de título que exibe o título da página atual.  
  
## <a name="example"></a>Exemplo  
 [!code-cpp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CPP/form1.cpp#0)]
 [!code-csharp[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/CS/form1.cs#0)]
 [!code-vb[System.Windows.Forms.WebBrowser#0](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.WebBrowser/VB/form1.vb#0)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies `System,``System.Drawing` e `System.Windows.Forms`.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Também é possível compilar este exemplo em [!INCLUDE[vsprvs](../../../../includes/vsprvs-md.md)] colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.WebBrowser>  
 [Controle WebBrowser](../../../../docs/framework/winforms/controls/webbrowser-control-windows-forms.md)
