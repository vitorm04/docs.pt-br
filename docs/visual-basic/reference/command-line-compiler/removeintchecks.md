---
title: /removeintchecks | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- removeintchecks
- /removeintchecks
dev_langs:
- VB
helpviewer_keywords:
- removeintchecks compiler option [Visual Basic]
- /removeintchecks compiler option [Visual Basic]
- -removeintchecks compiler option [Visual Basic]
ms.assetid: c1835bd5-1e38-4fba-bd2f-6984774765d4
caps.latest.revision: 14
author: dotnet-bot
ms.author: dotnetcontent
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
ms.openlocfilehash: 8e50200b8755ccc6b1c173024856955f5075b67e
ms.lasthandoff: 03/13/2017

---
# <a name="removeintchecks"></a>/removeintchecks
Ativa para operações de inteiros ou desativar a verificação de erro de estouro.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/removeintchecks[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`+` &#124; `-`|Opcional. O `/removeintchecks-` opção faz com que o compilador verifique todos os cálculos de número inteiro para erros de estouro. O padrão é `/removeintchecks-`.<br /><br /> Especificando `/removeintchecks` ou `/removeintchecks+` impede a verificação de erros e pode fazer cálculos de número inteiro mais rápidos. No entanto, sem a verificação de erros, e se estão estourou capacidades de tipo de dados, os resultados incorretos podem ser armazenados sem gerar um erro.|  
  
|Para definir /removeintchecks no Visual Studio ambiente de desenvolvimento integrado|  
|---|  
|1.  Tenha um projeto selecionado no **Solution Explorer**. No menu **Projeto**, clique em **Propriedades**. Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique na guia **Compilar**.<br />3.  Clique o **avançado** botão.<br />4.  Modificar o valor da **remover verificação de estouro de inteiro** caixa.|  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `Test.vb` e desativa a verificação de erro de estouro de inteiro.  
  
```  
vbc /removeintchecks+ test.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
