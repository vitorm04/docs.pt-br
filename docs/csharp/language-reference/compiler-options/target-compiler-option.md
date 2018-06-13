---
title: -target (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /target
helpviewer_keywords:
- target compiler options [C#]
- /target compiler options [C#]
- assemblies [C#], compiling
- -target compiler options [C#]
ms.assetid: a18bbd8e-bbf7-49e7-992c-717d0eb1f76f
ms.openlocfilehash: 7736b8850a7b09f7212e83e05acf0e1994bce0fe
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33215492"
---
# <a name="-target-c-compiler-options"></a>-target (opções do compilador C#)
A opção do compilador **-target** pode ser especificada em uma das quatro formas:  
  
 [/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
 Para criar um arquivo .exe para aplicativos [!INCLUDE[win8_appname_long](~/includes/win8-appname-long-md.md)].  
  
 [/target:exe](../../../csharp/language-reference/compiler-options/target-exe-compiler-option.md)  
 Para criar um arquivo .exe.  
  
 [/target:library](../../../csharp/language-reference/compiler-options/target-library-compiler-option.md)  
 Para criar uma biblioteca de códigos.  
  
 [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md)  
 Para criar um módulo.  
  
 [/target:winexe](../../../csharp/language-reference/compiler-options/target-winexe-compiler-option.md)  
 Para criar um programa do Windows.  
  
 [/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
 Para criar um arquivo .winmdobj intermediário.  
  
 A menos que você especifique **-target:module**, o **-target** faz com que um manifesto do assembly do .NET Framework seja colocado em um arquivo de saída. Para obter mais informações, consulte [Assemblies no Common Language Runtime](../../../framework/app-domains/assemblies-in-the-common-language-runtime.md) e [Atributos comuns](../../programming-guide/concepts/attributes/common-attributes.md).  
  
 O manifesto do assembly é colocado no primeiro arquivo de saída .exe na compilação ou na primeira DLL, se não houver nenhum arquivo de saída .exe. Por exemplo, na linha de comando a seguir, o manifesto será colocado em `1.exe`:  
  
```console  
csc -out:1.exe t1.cs -out:2.netmodule t2.cs  
```  
  
 O compilador cria apenas um manifesto do assembly por compilação. As informações sobre todos os arquivos em uma compilação são colocados no manifesto do assembly. Todos os arquivos de saída, exceto os criados com **-target:module** podem conter um manifesto do assembly. Ao gerar vários arquivos de saída na linha de comando, apenas um manifesto do assembly pode ser criado e ele deve ir para o primeiro arquivo de saída especificado na linha de comando. Não importa qual é o primeiro arquivo de saída (**-target:exe**, **-target:winexe**, **-target:library** ou **-target:module**), todos os outros arquivos de saída produzidos na mesma compilação devem ser módulos (**-target:module**).  
  
 Se você criar um assembly, pode indicar que todo ou parte do seu código está em conformidade com CLS com o atributo <xref:System.CLSCompliantAttribute>.  
  
```csharp  
// target_clscompliant.cs  
[assembly:System.CLSCompliant(true)]   // specify assembly compliance  
  
[System.CLSCompliant(false)]   // specify compliance for an element  
public class TestClass  
{  
    public static void Main() {}  
}  
```  
  
 Para obter mais informações sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)  
 [-subsystemversion (opções do compilador do C#)](../../../csharp/language-reference/compiler-options/subsystemversion-compiler-option.md)
