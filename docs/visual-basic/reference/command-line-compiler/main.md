---
title: -main
ms.date: 03/13/2018
helpviewer_keywords:
- main compiler option [Visual Basic]
- /main compiler option [Visual Basic]
- -main compiler option [Visual Basic]
ms.assetid: 83fc339d-6652-415d-b205-b5133319b5b0
ms.openlocfilehash: 91f2a27ed9b6fb296dbb9e50fc488fd012311890
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005500"
---
# <a name="-main"></a>-main
Especifica a classe ou o módulo que contém o procedimento `Sub Main`.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-main:location  
```  
  
## <a name="arguments"></a>Argumentos  
 `location`  
 Necessário. O nome da classe ou do módulo que contém o procedimento `Sub Main` a ser chamado quando o programa é iniciado. Isso pode estar no formato **-principal: módulo** ou **-principal: namespace. Module**.  
  
## <a name="remarks"></a>Comentários  
 Use essa opção quando você criar um arquivo executável ou programa executável do Windows. Se a opção **-Main** for omitida, o compilador pesquisará um `Sub Main` compartilhado válido em todas as classes e módulos públicos.  
  
 Consulte o [procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md) para obter uma discussão sobre as várias formas do procedimento `Main`.  
  
 Quando `location` é uma classe que herda de <xref:System.Windows.Forms.Form>, o compilador fornece um procedimento padrão `Main` que inicia o aplicativo se a classe não tiver um procedimento `Main`. Isso permite que você compile o código na linha de comando que foi criada no ambiente de desenvolvimento.  
  
 [!code-vb[VbVbalrCompiler#16](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/Class1.vb#16)]  
  
### <a name="to-set--main-in-the-visual-studio-integrated-development-environment"></a>Para definir o principal no ambiente de desenvolvimento integrado do Visual Studio  
  
1. Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**.  
  
2. Clique na guia **Aplicativo**.  
  
3. Verifique se a caixa de seleção **habilitar estrutura de aplicativo** não está marcada.  
  
4. Modifique o valor na caixa **objeto de inicialização** .  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` e `T3.vb`, especificando que o procedimento `Sub Main` será encontrado na classe `Test2`.  
  
```console
vbc t2.vb t3.vb -main:Test2  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Procedimento principal no Visual Basic](../../../visual-basic/programming-guide/program-structure/main-procedure.md)
