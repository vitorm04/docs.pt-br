---
title: -nostdlib (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /nostdlib
helpviewer_keywords:
- nostdlib compiler option [C#]
- -nostdlib compiler option [C#]
- /nostdlib compiler option [C#]
ms.assetid: ec197989-fa49-4725-a455-e06b551eb65f
ms.openlocfilehash: 70007c74efe9a41bdfc15e8fa7daf3c8fc0221ed
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/26/2018
ms.locfileid: "42935518"
---
# <a name="-nostdlib-c-compiler-options"></a>-nostdlib (opções do compilador C#)

**-nostdlib** impede a importação de mscorlib.dll, que define todo o namespace System.

## <a name="syntax"></a>Sintaxe

```console
-nostdlib[+ | -]
```

## <a name="remarks"></a>Comentários

Use essa opção se desejar definir ou criar seus próprios objetos e namespace System.

Se você não especificar **-nostdlib**, o mscorlib.dll será importado no programa (o mesmo que especificar **-nostdlib-**). Especificar **-nostdlib** é o mesmo que especificar **-nostdlib+**.

### <a name="to-set-this-compiler-option-in-visual-studio"></a>Para definir essa opção do compilador no Visual Studio

> [!NOTE]
> As instruções a seguir se aplicam apenas ao Visual Studio 2015 (e a versões anteriores). A propriedade de build **Não referenciar mscorlib.dll** não existe no Visual Studio 2017.

1. Abra a página **Propriedades** do projeto.

2. Clique na página de propriedades **Compilar**.

3. Clique no botão **Avançado**.

4. Modifique a propriedade **Não referenciar mscorlib.dll**.

### <a name="to-set-this-compiler-option-programmatically"></a>Para definir essa opção do compilador via programação

Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.NoStdLib%2A>.

## <a name="see-also"></a>Consulte também

- [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
