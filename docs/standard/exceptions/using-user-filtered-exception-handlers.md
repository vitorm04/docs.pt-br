---
title: "Usando manipuladores de exceções filtrados pelo usuário"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- user-filtered exceptions
- exceptions, user-filtered
ms.assetid: aa80d155-060d-41b4-a636-1ceb424afee8
caps.latest.revision: "10"
author: mairaw
ms.author: mairaw
manager: wpickett
ms.openlocfilehash: a71a722063448fb0d568f4bfb4f71d4e01c57454
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/18/2017
---
# <a name="using-user-filtered-exception-handlers"></a>Usando manipuladores de exceções filtrados pelo usuário
Atualmente, o Visual Basic suporta exceções filtradas pelo usuário. Os manipuladores de exceção filtrados por usuário capturam e tratam exceções com base nos requisitos que você define para a exceção. Esses manipuladores utiliza o **Catch** instrução com o **quando** palavra-chave.  
  
 Essa técnica é útil quando um objeto de exceção em particular corresponde a vários erros. Nesse caso, o objeto normalmente tem uma propriedade que contém o código de erro específico associado ao erro. Você pode usar a propriedade do código de erro na expressão para selecionar apenas o erro específico que você deseja manipular no que **Catch** cláusula.  
  
 O exemplo de Visual Basic a seguir ilustra o **Catch/quando** instrução.  
  
```  
Try  
      'Try statements.  
   Catch When Err = VBErr_ClassLoadException  
      'Catch statements.  
End Try  
```  
  
 A expressão da cláusula de filtro de usuário não é restrita de forma alguma. Se ocorrer uma exceção durante a execução da expressão de filtro de usuário, essa exceção será descartada e a expressão de filtro é considerada a ser avaliada como false. Nesse caso, o common language runtime continua a pesquisa para um manipulador para a exceção atual.  
  
## <a name="combining-the-specific-exception-and-the-user-filtered-clauses"></a>Combinando a exceção específica e as cláusulas de filtro de usuário  
 Uma instrução catch pode conter a exceção específica e as cláusulas de filtro de usuário. O tempo de execução testa a exceção específica pela primeira vez. Se a exceção específica for bem-sucedida, o tempo de execução executa o filtro de usuário. O filtro genérico pode conter uma referência à variável declarada no filtro de classe. Observe que a ordem das duas cláusulas de filtros não pode ser revertida.  
  
 O seguinte exemplo do Visual Basic mostra a exceção específica `ClassLoadException` no **Catch** instrução, bem como a cláusula de filtro de usuário usando o **quando** palavra-chave.  
  
```  
Try  
      'Try statements.  
   Catch cle As ClassLoadException When cle.IsRecoverable()  
      'Catch statements.  
End Try  
```  

## <a name="see-also"></a>Consulte também
[Exceções](index.md)
