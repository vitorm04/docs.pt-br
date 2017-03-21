---
title: /Main | Documentos do Microsoft
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
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
caps.latest.revision: 19
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
ms.openlocfilehash: dded7621845141896f353d69ab757010c825b975
ms.lasthandoff: 03/13/2017

---
# <a name="main"></a>/main
Especifica a classe ou o módulo que contém o procedimento `Sub Main`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/main:location  
```  
  
## <a name="arguments"></a>Arguments  
 `location`  
 Necessário. Um total de qualificação para a classe ou módulo que contém o `Sub Main` procedimento a ser chamado quando o programa for iniciado. Isso pode estar no formato **/main:module** ou **/Main**.  
  
## <a name="remarks"></a>Comentários  
 Use esta opção quando você cria um arquivo executável ou programa executável do Windows. Se o **/principal** opção for omitida, o compilador procura por um arquivo compartilhado `Sub Main` em todas as classes públicas e módulos.  
  
 Consulte [procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) para uma discussão sobre as diversas formas dos `Main` procedimento.  
  
 Quando `location` é uma classe que herda de <xref:System.Windows.Forms.Form>, o compilador fornece um padrão `Main` que inicia o aplicativo se a classe possui nenhum procedimento `Main` procedimento.</xref:System.Windows.Forms.Form> Isso lhe permite compilar código na linha de comando que foi criado no ambiente de desenvolvimento.  
  
 [!code-vb[VbVbalrCompiler n º&16;](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set-main-in-the-visual-studio-integrated-development-environment"></a>Para definir/principal no Visual Studio ambiente de desenvolvimento integrado  
  
1.  Tenha um projeto selecionado no **Solution Explorer**. No menu **Projeto**, clique em **Propriedades**.  
  
     Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).  
  
2.  Clique o **aplicativo** guia.  
  
3.  Verifique se o **estrutura do aplicativo ativar** caixa de seleção não estiver marcada.  
  
4.  Modificar o valor de **o objeto de inicialização** caixa.  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `T2.vb` e `T3.vb`, especificando que o `Sub Main` procedimento será encontrado na `Test2` classe.  
  
```  
vbc t2.vb t3.vb /main:Test2  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [NIB: versão do Visual Basic do Hello, World](http://msdn.microsoft.com/en-us/9d030b60-e148-4366-a462-69532f02294c)   
 [Procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
