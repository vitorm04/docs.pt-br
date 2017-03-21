---
title: "Refatoração e renomear a caixa de diálogo (Visual Basic) | Documentos do Microsoft"
ms.date: 2015-07-20
ms.prod: .net
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RenameSymbol
dev_langs:
- VB
helpviewer_keywords:
- symbols, renaming
- names, changing symbol
- Rename dialog box
ms.assetid: 001d2d81-9bb6-4e8e-ae3a-20c0daaa3959
redirect_url: https://msdn.microsoft.com/library/ckfya594(v=vs.140).aspx
caps.latest.revision: 11
author: stevehoag
ms.author: shoag
translation.priority.ht:
- cs-cz
- de-de
- es-es
- fr-fr
- it-it
- ja-jp
- ko-kr
- pl-pl
- pt-br
- ru-ru
- tr-tr
- zh-cn
- zh-tw
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8955fd2b6dcf413589efdd250965b85aa3c4a291
ms.lasthandoff: 03/13/2017

---
# <a name="refactoring-and-rename-dialog-box-visual-basic"></a>Caixa de diálogo Refatoração e Renomear (Visual Basic)
Usar interno do Visual Basic **Renomear** caixa de diálogo renomear identificadores em seu código para símbolos como campos, variáveis locais, métodos, namespaces, propriedades e tipos. Você pode abrir o **Renomear** caixa de diálogo clicando com a declaração de elemento.  
  
 **Novo nome**  
 Especifica o novo nome para o elemento de código.  
  
 **Local**  
 Identifica o namespace para pesquisar quando você executar a operação de renomeação.  
  
## <a name="rename-operations"></a>Operações de renomeação  
 O **Renomear** caixa de diálogo executa operações de renomeação ligeiramente diferentes, dependendo do tipo de elemento renomeado.  
  
|Tipo de elemento|Renomear a operação|  
|------------------|----------------------|  
|Classe|Altera todas as declarações e todos os usos da classe para o novo nome. Para classes parciais, a operação de renomeação se propaga para todas as partes.|  
|Campo|Altera a declaração e usos do campo para o novo nome.|  
|Variável local|Altera a declaração e usos da variável para o novo nome.|  
|Método|Altera o nome do método e todas as referências a esse método para o novo nome.|  
|espaço de nome|Altera o nome do namespace para o novo nome, na declaração, todos os `Imports` instruções e todos os nomes totalmente qualificados.|  
|Propriedade|Altera a declaração e usos da propriedade para o novo nome.|  
  
## <a name="refactoring"></a>Refatoração  
 Para fornecer uma experiência de refatoração mais completa, Visual Basic tem uma parceria com Developer Express Inc. para obter suporte à refatoração. Consulte [Refactor!](http://go.microsoft.com/fwlink/?LinkId=155788) no MSDN Visual Basic Developer Center para obter mais detalhes e instruções sobre como baixar a ferramenta. Refactor! oferece suporte a mais de 15 recursos individuais de refatoração. Isso inclui operações como reordenar parâmetros, extrair método, Encapsulate Field e Create Overload.  
  
## <a name="see-also"></a>Consulte também  
 [Usando o Ambiente de Desenvolvimento do Visual Basic](../../../visual-basic/developing-apps/using-ide/using-the-visual-basic-development-environment.md)
