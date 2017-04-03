---
title: "-optimize (Opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /optimize
dev_langs:
- CSharp
helpviewer_keywords:
- /optimize compiler option [C#]
- -o compiler option [C#]
- optimize compiler option [C#]
- /o compiler option [C#]
- -optimize compiler option [C#]
- compiler optimization [C#]
- o compiler option [C#]
ms.assetid: 6dd5b6f2-cd1d-4593-a9f4-1c2ed9404ca0
caps.latest.revision: 15
author: BillWagner
ms.author: wiwagn
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
translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: d9eefdd57855d4d9adea2d8a17cb4d90cc9972f5
ms.lasthandoff: 03/13/2017

---
# <a name="optimize-c-compiler-options"></a>/optimize (opções do compilador C#)
A opção **/optimize** habilita ou desabilita otimizações executadas pelo compilador para tornar o arquivo de saída menor, mais rápido e mais eficiente.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/optimize[+ | -]  
```  
  
## <a name="remarks"></a>Comentários  
 A **/optimize** também informa o Common Language Runtime para otimizar o código em tempo de execução.  
  
 Por padrão, as otimizações estão desabilitadas. Especifique **/optimize+** para habilitar otimizações.  
  
 Ao criar um módulo a ser usado por um assembly, use as mesmas configurações **/optimize** que as do assembly.  
  
 **/o** é a forma abreviada de **/optimize**.  
  
 É possível combinar as opções **/optimize** e [/debug](../../../csharp/language-reference/compiler-options/debug-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades **Compilar**.  
  
3.  Modifique a propriedade **Otimizar código**.  
  
 Para obter informações sobre como definir essa opção do compilador de maneira programática, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.  
  
## <a name="example"></a>Exemplo  
 Compile `t2.cs` e habilite as otimizações do compilador:  
  
```  
csc t2.cs /optimize  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB: como modificar as propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
