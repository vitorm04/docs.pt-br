---
title: /Imports (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- /imports compiler option [Visual Basic]
- imports compiler option [Visual Basic]
- -imports compiler option [Visual Basic]
ms.assetid: 9a93fb53-c080-497b-bf9b-441022dbbc39
caps.latest.revision: 15
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
ms.openlocfilehash: 1dcbba442413dba63aef31fd40a511bad5e8217b
ms.lasthandoff: 03/13/2017

---
# <a name="imports-visual-basic"></a>/imports (Visual Basic)
Importa namespaces de um assembly especificado.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/imports:namespaceList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`namespaceList`|Necessário. Lista delimitada por vírgula de namespaces a serem importados.|  
  
## <a name="remarks"></a>Comentários  
 O `/imports` opção importa qualquer namespace definido no interior do conjunto atual de arquivos de origem ou de qualquer assembly referenciado.  
  
 Os membros no namespace especificado com `/imports` estão disponíveis para todos os arquivos de código-fonte na compilação. Use o [instrução Imports (tipo e Namespace .NET)](../../../visual-basic/language-reference/statements/imports-statement-net-namespace-and-type.md) para utilizar um namespace em um arquivo de código-fonte única.  
  
|Para configurar /Imports no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Tenha um projeto selecionado no **Solution Explorer**. No menu **Projeto**, clique em **Propriedades**. Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique o **referências** guia.<br />3.  Insira o nome do namespace na caixa ao lado de **Add User Import** botão.<br />4.  Clique o **Add User Import** botão.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila quando `/imports:system` for especificado.  
  
 [!code-vb[VbVbalrCompiler&#21;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/imports_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Referências e a instrução Imports](../../../visual-basic/programming-guide/program-structure/references-and-the-imports-statement.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
