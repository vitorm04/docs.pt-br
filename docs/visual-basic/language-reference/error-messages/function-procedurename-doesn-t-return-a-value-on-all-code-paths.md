---
title: A função '<procedurename>' não retorna um valor em todos os caminhos de código
ms.date: 07/20/2015
f1_keywords:
- bc42105
- vbc42105
helpviewer_keywords:
- BC42105
ms.assetid: b6929bf4-a365-4a70-8dc9-6b0fc09e1468
ms.openlocfilehash: badcfea4f24ba3858071e02ba47b8f77ab557f88
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "61802369"
---
# <a name="function-procedurename-doesnt-return-a-value-on-all-code-paths"></a>Função '\<procedurename >' não retorna um valor em todos os caminhos de código
Função '\<procedurename >' não retorna um valor em todos os caminhos de código. Está faltando uma instrução 'Return'?  
  
 Um `Function` procedimento tem pelo menos um caminho possível pelo seu código que não retorna um valor.  
  
 Você pode retornar um valor de uma `Function` procedimento em qualquer uma das seguintes maneiras:  
  
- Incluir o valor em uma [instrução Return](../../../visual-basic/language-reference/statements/return-statement.md).  
  
- Atribua o valor para o `Function` procedimento nomear e, em seguida, executar um `Exit Function` instrução.  
  
- Atribua o valor para o `Function` procedimento nomear e, em seguida, execute o `End Function` instrução.  
  
 Se o controle passa para `Exit Function` ou `End Function` e você não tiver atribuído qualquer valor para o nome do procedimento, o procedimento retornará o valor padrão do tipo de dados de retorno. Para obter mais informações, consulte "Comportamento" em [instrução Function](../../../visual-basic/language-reference/statements/function-statement.md).  
  
 Por padrão, esta mensagem é um aviso. Para obter mais informações sobre como ocultar avisos ou tratar avisos como erros, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
 **ID do erro:** BC42105  
  
## <a name="to-correct-this-error"></a>Para corrigir este erro  
  
- Verifique sua lógica de fluxo de controle e verifique se que você atribuir um valor antes de cada instrução que faz com que um retorno.  
  
     É mais fácil garantir que cada retorno do procedimento retorna um valor se você usar sempre o `Return` instrução. Se você fizer isso, a última instrução antes `End Function` deve ser um `Return` instrução.  
  
## <a name="see-also"></a>Consulte também

- [Procedimentos de Função](../../../visual-basic/programming-guide/language-features/procedures/function-procedures.md)
- [Instrução Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Página de Compilação, Designer de Projeto (Visual Basic)](/visualstudio/ide/reference/compile-page-project-designer-visual-basic)
