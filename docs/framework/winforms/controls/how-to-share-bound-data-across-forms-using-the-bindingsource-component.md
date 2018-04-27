---
title: Como compartilhar dados associados entre formulários usando o componente BindingSource
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
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
caps.latest.revision: 8
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1907f25e2d9bfe5fc6e93020add47d8a52379e87
ms.sourcegitcommit: 2042de78fcdceebb6b8ac4b7a292b93e8782cbf5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/27/2018
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a>Como compartilhar dados associados entre formulários usando o componente BindingSource
Você pode facilmente compartilhar dados entre formulários usando o <xref:System.Windows.Forms.BindingSource> componente. Por exemplo, talvez você queira exibir um formulário de somente leitura que resume os dados de origem de dados e outro formulário editável que contém informações detalhadas sobre o item atualmente selecionado na fonte de dados. Este exemplo demonstra esse cenário.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como compartilhar um <xref:System.Windows.Forms.BindingSource> e seus dados associados entre formulários. Neste exemplo, compartilhado <xref:System.Windows.Forms.BindingSource> é passado para o construtor do formulário filho. O formulário filho permite que o usuário edite os dados para o atualmente item selecionado no formulário principal.  
  
> [!NOTE]
>  O <xref:System.Windows.Forms.BindingSource.BindingComplete> eventos para o <xref:System.Windows.Forms.BindingSource> componente é tratado no exemplo para garantir que as duas formas permaneçam sincronizadas. Para obter mais informações sobre o motivo de isso ser feito, consulte [Como assegurar que vários controles associados à mesma fonte de dados permaneçam sincronizados](../../../../docs/framework/winforms/multiple-controls-bound-to-data-source-synchronized.md).  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
-   Referências aos assemblies System, System.Windows.Forms, System.Drawing, System.Data e System.Xml.  
  
 Para obter informações sobre como criar este exemplo da linha de comando para o Visual Basic ou Visual c#, consulte [Compilando a partir da linha de comando](~/docs/visual-basic/reference/command-line-compiler/building-from-the-command-line.md) ou [criação de linha de comando com csc.exe](~/docs/csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Você também pode criar este exemplo no Visual Studio colando o código em um novo projeto.  Consulte também [Como compilar e executar um exemplo completo de código do Windows Forms usando o Visual Studio](http://msdn.microsoft.com/library/Bb129228\(v=vs.110\)).  
  
## <a name="see-also"></a>Consulte também  
 [Componente BindingSource](../../../../docs/framework/winforms/controls/bindingsource-component.md)  
 [Associação de dados do Windows Forms](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 [Como identificar erros e exceções que ocorram na associação de dados](../../../../docs/framework/winforms/controls/how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
