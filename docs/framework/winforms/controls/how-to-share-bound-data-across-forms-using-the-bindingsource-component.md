---
title: 'Como: Compartilhar dados associados entre formulários usando o componente BindingSource'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- examples [Windows Forms], BindingSource component
- data binding [Windows Forms], sharing data across forms
- BindingSource component [Windows Forms], examples
- BindingSource [Windows Forms], using with multiple forms
ms.assetid: a1a49630-db9c-4485-b888-1f62a373a4f7
ms.openlocfilehash: aa497194fd4ac65f48773a45175333a1d862b453
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/22/2019
ms.locfileid: "69956069"
---
# <a name="how-to-share-bound-data-across-forms-using-the-bindingsource-component"></a>Como: Compartilhar dados associados entre formulários usando o componente BindingSource
Você pode facilmente compartilhar dados em formulários usando o <xref:System.Windows.Forms.BindingSource> componente. Por exemplo, talvez você queira exibir um formulário de somente leitura que resume os dados de origem de dados e outro formulário editável que contém informações detalhadas sobre o item atualmente selecionado na fonte de dados. Este exemplo demonstra esse cenário.  
  
## <a name="example"></a>Exemplo  
 O exemplo de código a seguir demonstra como compartilhar <xref:System.Windows.Forms.BindingSource> um e seus dados vinculados em formulários. Neste exemplo, o compartilhado <xref:System.Windows.Forms.BindingSource> é passado para o construtor do formulário filho. O formulário filho permite que o usuário edite os dados para o atualmente item selecionado no formulário principal.  
  
> [!NOTE]
> O <xref:System.Windows.Forms.BindingSource.BindingComplete> evento para o <xref:System.Windows.Forms.BindingSource> componente é tratado no exemplo para garantir que os dois formulários permaneçam sincronizados. Para obter mais informações sobre por que isso é feito [, consulte Como: Verifique se vários controles vinculados à mesma fonte de dados](../multiple-controls-bound-to-data-source-synchronized.md)permanecem sincronizados.  
  
 [!code-csharp[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/CS/Form1.cs#1)]
 [!code-vb[System.Windows.Forms.BindingSourceMultipleForms#1](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.BindingSourceMultipleForms/VB/Form1.vb#1)]  
  
## <a name="compiling-the-code"></a>Compilando o código  
 Este exemplo requer:  
  
- Referências aos assemblies System, System.Windows.Forms, System.Drawing, System.Data e System.Xml.  
  
## <a name="see-also"></a>Consulte também

- [Componente BindingSource](bindingsource-component.md)
- [Associação de dados do Windows Forms](../windows-forms-data-binding.md)
- [Como: Tratar erros e exceções que ocorrem com DataBinding](how-to-handle-errors-and-exceptions-that-occur-with-databinding.md)
