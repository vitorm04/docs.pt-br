---
title: -unsafe (opções do compilador C#)
ms.date: 04/25/2018
f1_keywords:
- /unsafe
helpviewer_keywords:
- -unsafe compiler option [C#]
- unsafe compiler option [C#]
- /unsafe compiler option [C#]
ms.openlocfilehash: 146299fda103567b111c66400c17edf36addd843
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/14/2020
ms.locfileid: "65877987"
---
# <a name="-unsafe-c-compiler-options"></a>-unsafe (opções do compilador C#)

A opção do compilador **-unsafe** permite que o código que usa a palavra-chave [unsafe](../keywords/unsafe.md) seja compilado.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-unsafe  
```  
  
## <a name="remarks"></a>Comentários

Para obter mais informações sobre código não seguro, consulte [Código não seguro e ponteiros](../../programming-guide/unsafe-code-pointers/index.md).  
  
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
  
## <a name="see-also"></a>Confira também

- [C# Opções de compilador](index.md)
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
