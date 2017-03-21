---
title: /optionexplicit | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /optionexplicit
dev_langs:
- VB
helpviewer_keywords:
- /optionexplicit compiler option [Visual Basic]
- optionexplicit compiler option [Visual Basic]
- -optionexplicit compiler option [Visual Basic]
ms.assetid: 5d296ab3-bafe-4c4d-9887-78f162ed86c7
caps.latest.revision: 16
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
ms.openlocfilehash: cfdad72c21b7886f9ea8a2d46e7c457087e7049d
ms.lasthandoff: 03/13/2017

---
# <a name="optionexplicit"></a>/optionexplicit
Faz com que o compilador reporte erros se variáveis não são declaradas antes de serem usadas.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/optionexplicit[+ | -]  
```  
  
## <a name="arguments"></a>Arguments  
 `+` &#124; `-`  
 Opcional. Especifique `/optionexplicit+` para requisitar declarações explícitas de variáveis. O `/optionexplicit+` opção é o padrão e é o mesmo que `/optionexplicit`. O `/optionexplicit-` opção permite declarações implícitas de variáveis.  
  
## <a name="remarks"></a>Comentários  
 Se o arquivo de código fonte contém uma [instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md), a instrução substitui a `/optionexplicit` configuração do compilador de linha de comando.  
  
### <a name="to-set-optionexplicit-in-the-visual-studio-ide"></a>Para definir /optionexplicit na IDE do Visual Studio  
  
1.  Tenha um projeto selecionado no **Solution Explorer**. No menu **Projeto**, clique em **Propriedades**. Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Clique na guia **Compilar**.  
  
3.  Modificar o valor de **Option Explicit** caixa.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila quando `/optionexplicit-` é usado.  
  
 [!code-vb[VbVbalrCompiler n º&5;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/optionexplicit_1.vb)]  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/optioncompare](../../../visual-basic/reference/command-line-compiler/optioncompare.md)   
 [/optionstrict](../../../visual-basic/reference/command-line-compiler/optionstrict.md)   
 [/optioninfer](../../../visual-basic/reference/command-line-compiler/optioninfer.md)   
 [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Instrução Option Explicit](../../../visual-basic/language-reference/statements/option-explicit-statement.md)   
 [Caixa de diálogo Padrões do Visual Basic, Projetos, Opções](https://docs.microsoft.com/visualstudio/ide/reference/visual-basic-defaults-projects-options-dialog-box)
