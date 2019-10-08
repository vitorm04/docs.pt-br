---
title: -addmodule
ms.date: 03/09/2018
helpviewer_keywords:
- /addmodule compiler option [Visual Basic]
- addmodule compiler option [Visual Basic]
- -addmodule compiler option [Visual Basic]
ms.assetid: fb4b89d4-4926-4f20-868d-427fa28497b2
ms.openlocfilehash: fbe3634d1fbc03acd56ef7276d65fd54493b9806
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002420"
---
# <a name="-addmodule"></a>-addmodule
Faz com que o compilador verifique todos os tipos de informações de arquivos especificados disponíveis para o projeto que você está compilando.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-addmodule:fileList  
```  
  
## <a name="arguments"></a>Argumentos  
 `fileList`  
 Necessário. Lista delimitada por vírgulas de arquivos que contêm metadados, mas não contêm manifestos de assembly. Os nomes de arquivo que contêm espaços devem estar entre aspas ("").  
  
## <a name="remarks"></a>Comentários  
 Os arquivos listados pelo parâmetro `fileList` devem ser criados com a opção `-target:module`, ou com o equivalente de outro compilador a `-target:module`.  
  
 Todos os módulos adicionados com `-addmodule` devem estar no mesmo diretório que o arquivo de saída em tempo de execução. Ou seja, você pode especificar um módulo em qualquer diretório em tempo de compilação, mas o módulo deve estar no diretório do aplicativo em tempo de execução. Se não for, você obterá um erro <xref:System.TypeLoadException>.  
  
 Se você especificar (implícita ou explicitamente) qualquer opção[-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md) diferente de `-target:module` com `-addmodule`, os arquivos passados para `-addmodule` se tornarão parte do assembly do projeto. Um assembly é necessário para executar um arquivo de saída que tem um ou mais arquivos adicionados com `-addmodule`.  
  
 Use [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md) para importar metadados de um arquivo que contém um assembly.  
  
> [!NOTE]
> A opção `-addmodule` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir cria um módulo.  
  
 [!code-vb[VbVbalrCompiler#47](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#47)]  
  
 O código a seguir importa os tipos do módulo.  
  
 [!code-vb[VbVbalrCompiler#48](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCompiler/VB/OptionStrictOff.vb#48)]  
  
 Quando você executa `t1`, ele gera `802`.  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [-Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)
- [-referência (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
