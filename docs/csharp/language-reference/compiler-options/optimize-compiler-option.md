---
title: "-optimize (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /optimize
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 2cf6919ee2d4f0a4031e18d46b9e5ebaf816b120
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-optimize-c-compiler-options"></a>-optimize (opções do compilador C#)
A opção **-optimize** habilita ou desabilita otimizações executadas pelo compilador para tornar o arquivo de saída menor, mais rápido e mais eficiente.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-optimize[+ | -]  
```  
  
## <a name="remarks"></a>Comentários  
 A **-optimize** também informa o Common Language Runtime para otimizar o código em tempo de execução.  
  
 Por padrão, as otimizações estão desabilitadas. Especifique **-optimize+** para habilitar otimizações.  
  
 Ao criar um módulo a ser usado por um assembly, use as mesmas configurações **-optimize** que as do assembly.  
  
 **-o** é a forma abreviada de **-optimize**.  
  
 É possível combinar as opções **-optimize** e [-debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades **Compilar**.  
  
3.  Modifique a propriedade **Otimizar código**.  
  
 Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.  
  
## <a name="example"></a>Exemplo  
 Compile `t2.cs` e habilite as otimizações do compilador:  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
