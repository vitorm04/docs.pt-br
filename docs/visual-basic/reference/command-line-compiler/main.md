---
title: -principal
ms.date: 03/13/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b22b4bb1b6649265eabc02beb6b0145f7c075b27
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-main"></a>-principal
Especifica a classe ou o módulo que contém o procedimento `Sub Main`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-main:location  
```  
  
## <a name="arguments"></a>Arguments  
 `location`  
 Necessário. O nome da classe ou módulo que contém o `Sub Main` procedimento a ser chamado quando o programa for iniciado. Isso pode estar no formato **-principal: módulo** ou **-main:namespace.module**.  
  
## <a name="remarks"></a>Comentários  
 Use esta opção quando você cria um arquivo executável ou programa executável do Windows. Se o **-principal** opção for omitida, o compilador procura por válido compartilhado `Sub Main` em todas as classes públicas e módulos.  
  
 Consulte [procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) para uma discussão sobre as várias formas da `Main` procedimento.  
  
 Quando `location` é uma classe que herda de <xref:System.Windows.Forms.Form>, o compilador fornece um padrão `Main` procedimento que inicia o aplicativo se a classe não tiver nenhuma `Main` procedimento. Isso permite que você compilar código na linha de comando que foi criado no ambiente de desenvolvimento.  
  
 [!code-vb[VbVbalrCompiler#16](../../../visual-basic/reference/command-line-compiler/codesnippet/VisualBasic/main_1.vb)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>Para definir - principal no ambiente de desenvolvimento integrado do Visual Studio  
  
1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.  
  
2.  Clique na guia **Aplicativo**.  
  
3.  Verifique se o **habilitar estrutura de aplicativo** caixa de seleção não está marcada.  
  
4.  Modificar o valor de **objeto de inicialização** caixa.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` e `T3.vb`, especificando que o `Sub Main` procedimento será localizado no `Test2` classe.  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [-alvo (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)  
 [Procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
