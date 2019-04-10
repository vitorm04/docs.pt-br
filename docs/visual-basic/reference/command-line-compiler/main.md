---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: fd6240faf702ccb5e543bfd6a7779284f38d8850
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337234"
---
# <a name="-main"></a>-main
Especifica a classe ou o módulo que contém o procedimento `Sub Main`.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-main:location  
```  
  
## <a name="arguments"></a>Arguments  
 `location`  
 Necessário. O nome da classe ou módulo que contém o `Sub Main` procedimento a ser chamado quando o programa é iniciado. Isso pode ser na forma **-principal: module** ou **-main:namespace.module**.  
  
## <a name="remarks"></a>Comentários  
 Use esta opção quando você cria um arquivo executável ou programa executável do Windows. Se o **-principal** opção for omitida, o compilador pesquisa válido compartilhado `Sub Main` em todas as classes públicas e módulos.  
  
 Ver [procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) para uma discussão sobre as várias formas dos `Main` procedimento.  
  
 Quando `location` é uma classe que herda <xref:System.Windows.Forms.Form>, o compilador fornece um padrão `Main` procedimento que inicia o aplicativo se a classe não tem nenhum `Main` procedimento. Isso permite que você compilar o código na linha de comando que foi criado no ambiente de desenvolvimento.  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>Para definir - principal no ambiente de desenvolvimento integrado do Visual Studio  
  
1. Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.  
  
2. Clique na guia **Aplicativo**.  
  
3. Verifique se o **habilitar estrutura de aplicativo** caixa de seleção não estiver marcada.  
  
4. Modificar o valor de **objeto de inicialização** caixa.  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `T2.vb` e `T3.vb`, especificando que o `Sub Main` procedimento será encontrado na `Test2` classe.  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Linhas de comando de compilação de exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
