---
title: Como identificar erros e exceções que ocorram na associação de dados
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
- error handling [Windows Forms], examples
- data binding [Windows Forms], examples
- examples [Windows Forms], error handling
- error handling [Windows Forms], data binding
- data binding [Windows Forms], error handling
- BindingSource component [Windows Forms], handling errors and exceptions
ms.assetid: eddc5bad-9513-47df-ab28-f02d8dff7892
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: f23743ecd37e36d2782cc6d6d8ff69448c8d334c
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-handle-errors-and-exceptions-that-occur-with-databinding"></a>Como identificar erros e exceções que ocorram na associação de dados
Muitas vezes, erros e exceções ocorrem nos objetos de negócios subjacentes quando você os associa aos controles. Você pode interceptar esses erros e exceções e, em seguida, recuperar ou passar as informações de erro para o usuário manipulando o <xref:System.Windows.Forms.Binding.BindingComplete> eventos para um determinado <xref:System.Windows.Forms.Binding>, <xref:System.Windows.Forms.BindingSource>, ou <xref:System.Windows.Forms.CurrencyManager> componente.  
  
## <a name="example"></a>Exemplo  
 Este exemplo de código demonstra como tratar erros e exceções que ocorrem durante uma operação de associação de dados. Demonstra como interceptar erros manipulando o <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> evento o <xref:System.Windows.Forms.Binding> objetos. Para interceptar erros e exceções ao manipular esse evento, você deve habilitar a formatação para a associação. Você pode habilitar a formatação quando a associação é construída ou adicionada à coleção de associação, ou definindo o <xref:System.Windows.Forms.Binding.FormattingEnabled%2A> propriedade `true`.  
  
 [!code-cpp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/cpp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CPP/form1.cpp#3)]
 [!code-csharp[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/CS/form1.cs#3)]
 [!code-vb[System.Windows.Forms.DataConnectorBindingComplete#3](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataConnectorBindingComplete/VB/form1.vb#3)]  
  
 Quando o código está em execução e uma cadeia de caracteres vazia é inserida para o nome da peça ou um valor menor que 100 é inserido para o número de peça, uma caixa de mensagem será exibida. Este é um resultado de tratamento de <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType> evento para essas associações de caixa de texto.  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Drawing e System.Windows.Forms.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 <xref:System.Windows.Forms.Binding.BindingComplete?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.BindingSource.BindingComplete?displayProperty=nameWithType>  
 [Componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)
