---
title: -define (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /define
helpviewer_keywords:
- -define compiler option [C#]
- /define compiler option [C#]
- -d compiler option [C#]
- define compiler option [C#]
- /d compiler option [C#]
- d compiler option [C#]
ms.assetid: f17d7b4d-82d0-4133-8563-68cced1cac6e
ms.openlocfilehash: 46ceca3a84e8ffbe6d07886c1b93d062f3ccd2d1
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "59305254"
---
# <a name="-define-c-compiler-options"></a>-define (opções do compilador C#)
A opção **-define** define `name` como um símbolo em todos os arquivos de código-fonte do seu programa.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-define:name[;name2]  
```  
  
## <a name="arguments"></a>Arguments  
 `name`, `name2`  
 O nome de um ou mais símbolos que você deseja definir.  
  
## <a name="remarks"></a>Comentários  
 A opção **-define** tem o mesmo efeito que usar uma diretiva de pré-processador [#define](../../../csharp/language-reference/preprocessor-directives/preprocessor-define.md), exceto que a opção do compilador está em vigor para todos os arquivos no projeto. Um símbolo permanece definido em um arquivo de origem até que uma diretiva [#undef](../../../csharp/language-reference/preprocessor-directives/preprocessor-undef.md) remova a definição no arquivo de origem. Quando você usa a opção -define, uma diretiva `#undef` em um arquivo não terá nenhum efeito em outros arquivos de código-fonte no projeto.  
  
 Você pode usar os símbolos criados por essa opção com [#if](../../../csharp/language-reference/preprocessor-directives/preprocessor-if.md), [#else](../../../csharp/language-reference/preprocessor-directives/preprocessor-else.md), [#elif](../../../csharp/language-reference/preprocessor-directives/preprocessor-elif.md) e [#endif](../../../csharp/language-reference/preprocessor-directives/preprocessor-endif.md) para compilar os arquivos de origem condicionalmente.  
  
 **-d** é a forma abreviada de **-define**.  
  
 Você pode definir vários símbolos com **-define**, usando um ponto e vírgula ou uma vírgula para separar os nomes dos símbolos. Por exemplo:  
  
```console  
-define:DEBUG;TUESDAY  
```  
  
 O compilador do C# não define símbolos ou macros que podem ser usados em seu código-fonte. Todas as definições de símbolo devem ser definidas pelo usuário.  
  
> [!NOTE]
>  O `#define` do C# não permite que um valor seja dado a um símbolo, como nas linguagens como a C++. Por exemplo, `#define` não pode ser usado para criar uma macro ou para definir uma constante. Se você precisar definir uma constante, use uma variável `enum`. Se você quiser criar uma macro de estilo C++, considere alternativas como os genéricos. Como as macros são notoriamente propensas a erros, o C# não permite o uso delas, mas oferece alternativas mais seguras.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1. Abra a página **Propriedades** do projeto.  
  
2. Na guia **Build**, digite o símbolo que deve ser definido na caixa **Símbolos de build condicional**. Por exemplo, se você estiver usando o exemplo de código a seguir, basta digitar `xx` na caixa de texto.  
  
 Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DefineConstants%2A>.  
  
## <a name="example"></a>Exemplo  
  
```csharp  
// preprocessor_define.cs  
// compile with: -define:xx  
// or uncomment the next line  
// #define xx  
using System;  
public class Test   
{  
    public static void Main()   
    {  
        #if (xx)   
            Console.WriteLine("xx defined");  
        #else  
            Console.WriteLine("xx not defined");  
        #endif  
    }  
}  
```  
  
## <a name="see-also"></a>Consulte também

- [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
