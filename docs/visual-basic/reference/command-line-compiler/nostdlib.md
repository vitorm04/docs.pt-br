---
title: -nostdlib
ms.date: 03/13/2018
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
ms.openlocfilehash: db6b047f521d8ef44d2bd1b70b654a4233ebb1a7
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347906"
---
# <a name="-nostdlib-visual-basic"></a>-nostdlib (Visual Basic)
Faz com que o compilador não referencie automaticamente as bibliotecas padrão.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-nostdlib  
```  
  
## <a name="remarks"></a>Comentários  
 A opção `-nostdlib` remove a referência automática para o assembly System. dll e impede que o compilador Leia o arquivo Vbc. rsp. O arquivo Vbc. rsp, localizado no mesmo diretório que o arquivo Vbc. exe, faz referência aos assemblies de .NET Framework usados com frequência e importa os namespaces de `System` e `Microsoft.VisualBasic`.  
  
> [!NOTE]
> Os assemblies mscorlib. dll e Microsoft. VisualBasic. dll são sempre referenciados.  
  
> [!NOTE]
> A opção `-nostdlib` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` sem fazer referência às bibliotecas padrão. Você deve definir o `_MYTYPE` constante de compilação condicional para a cadeia de caracteres "Empty" para remover o objeto `My`.  
  
```console
vbc -nostdlib -define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [-noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)
- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Personalizando quais objetos estão disponíveis em My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
