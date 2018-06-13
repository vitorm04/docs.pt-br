---
title: -target:library (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /dll
helpviewer_keywords:
- -target compiler options [C#], /target:library
- target compiler options [C#], /target:library
- /target compiler options [C#], /target:library
ms.assetid: c5670e88-2126-47c1-8d1c-217923837d17
ms.openlocfilehash: 39f6ad5839f7ca12b023502a3fc1ccde52e70899
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215343"
---
# <a name="-targetlibrary-c-compiler-options"></a>-target:library (opções do compilador C#)
A opção **-target:library** faz com que o compilador crie uma DLL (biblioteca de vínculo dinâmico) em vez de um EXE (arquivo executável).  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-target:library  
```  
  
## <a name="remarks"></a>Comentários  
 A DLL será criada com a extensão .dll.  
  
 A menos que seja especificado de outra forma com a opção [-out](../../../csharp/language-reference/compiler-options/out-compiler-option.md), o nome do arquivo de saída usa o nome do primeiro arquivo de entrada.  
  
 Quando especificado na linha de comando, todos os arquivos até a próxima opção **-out** ou **-target:module** são usados para criar o arquivo .dll.  
  
 Ao criar um arquivo .dll, um método [Main](../../../csharp/programming-guide/main-and-command-args/index.md) não é necessário.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades do **Aplicativo**.  
  
3.  Modifique a propriedade **Tipo de saída**.  
  
 Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Exemplo  
 Compile `in.cs`, criando `in.dll`:  
  
```console  
csc -target:library in.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [-target (opções do compilador do C#)](../../../csharp/language-reference/compiler-options/target-compiler-option.md)  
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
