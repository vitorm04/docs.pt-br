---
description: -optimize (opções do compilador C#)
title: -optimize (opções do compilador C#)
ms.date: 07/20/2015
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
ms.openlocfilehash: 6fd268414c4e54e7b4865733480f8917389015d0
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89125027"
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
  
 É possível combinar as opções **-optimize** e [-debug](./debug-compiler-option.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1. Abra a página **Propriedades** do projeto.  
  
2. Clique na página de propriedades **Compilar**.  
  
3. Modifique a propriedade **Otimizar código**.  
  
 Para obter informações sobre como definir essa opção do compilador programaticamente, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.Optimize%2A>.  
  
## <a name="example"></a>Exemplo  
 Compile `t2.cs` e habilite as otimizações do compilador:  
  
```console  
csc t2.cs -optimize  
```  
  
## <a name="see-also"></a>Confira também

- [Opções do compilador C#](./index.md)
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
