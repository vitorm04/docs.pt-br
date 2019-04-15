---
title: -unsafe (opções do compilador C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 4cfd7c82bc2cbf816164b235642c0647eeb7e5b6
ms.sourcegitcommit: 558d78d2a68acd4c95ef23231c8b4e4c7bac3902
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/09/2019
ms.locfileid: "59337325"
---
# <a name="-unsafe-c-compiler-options"></a>-unsafe (opções do compilador C#)
A opção do compilador **-unsafe** permite que o código que usa a palavra-chave [unsafe](../../../csharp/language-reference/keywords/unsafe.md) seja compilado.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a>Comentários  
 Para obter mais informações sobre código não seguro, consulte [Código não seguro e ponteiros](../../../csharp/programming-guide/unsafe-code-pointers/index.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1. Abra a página **Propriedades** do projeto.  
  
2. Clique na página de propriedades **Compilar**.  
  
3. Marque a caixa de seleção **Permitir código não seguro**.  
  
### <a name="to-add-this-option-in-a-csproj-file"></a>Para adicionar essa opção em um arquivo csproj

Abra o arquivo .csproj de um projeto e adicione os seguintes elementos:

```xml
  <PropertyGroup>
    <AllowUnsafeBlocks>true</AllowUnsafeBlocks>
  </PropertyGroup>
```

 Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.AllowUnsafeBlocks%2A>.  
  
## <a name="example"></a>Exemplo  
 Compile `in.cs` para o modo não seguro:  
  
```console  
csc -unsafe in.cs  
```  
  
## <a name="see-also"></a>Consulte também

- [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
- [Gerenciando propriedades de solução e projeto](/visualstudio/ide/managing-project-and-solution-properties)
