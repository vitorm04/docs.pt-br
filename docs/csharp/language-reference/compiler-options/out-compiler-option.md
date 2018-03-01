---
title: "-out (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /out
helpviewer_keywords:
- /out compiler option [C#]
- out compiler option [C#]
- -out compiler option [C#]
ms.assetid: 70d91d01-7bd2-4aea-ba8b-4e9807e9caa5
caps.latest.revision: 
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: 8ca85293086f8747cc4aaff02e7d9b5628b1e88a
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-out-c-compiler-options"></a>-out (opções do compilador C#)
A opção **-out** especifica o nome do arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-out:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 O nome do arquivo de saída criado pelo compilador.  
  
## <a name="remarks"></a>Comentários  
 Na linha de comando, é possível especificar vários arquivos de saída para a compilação. O compilador espera encontrar um ou mais arquivos de código-fonte após a opção **-out**. Em seguida, todos os arquivos de código-fonte serão compilados no arquivo de saída especificado por essa opção **-out**.  
  
 Especifique o nome completo e a extensão do arquivo que você deseja criar.  
  
 Se você não especificar o nome do arquivo de saída:  
  
-   Um .exe extrairá seu nome do arquivo de código-fonte que contém o método **principal**.  
  
-   Um arquivo .dll ou .netmodule extrairá seu nome do primeiro arquivo de código-fonte.  
  
 Um arquivo de código-fonte usado para compilar um arquivo de saída não pode ser usado na mesma compilação para a compilação de outro arquivo de saída.  
  
 Ao produzir vários arquivos de saída em uma compilação de linha de comando, tenha em mente que somente um dos arquivos de saída pode ser um assembly e que somente o primeiro arquivo de saída especificado (implícita ou explicitamente com **-out**) pode ser o assembly.  
  
 Os módulos produzidos como parte de uma compilação se tornam arquivos associados a qualquer assembly também produzido na compilação. Use [ildasm.exe](../../../framework/tools/ildasm-exe-il-disassembler.md) para exibir o manifesto do assembly para ver os arquivos associados.  
  
 A opção do compilador -out é necessária para que um exe seja o destino de um assembly amigável. Para obter mais informações, consulte [Assemblies amigáveis](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades do **Aplicativo**.  
  
3.  Modifique a propriedade **Nome do Assembly**.  
  
     Para definir essa opção do compilador de maneira programática: <xref:VSLangProj80.ProjectProperties3.OutputFileName%2A> é uma propriedade somente leitura, determinada por uma combinação do tipo de projeto (exe, biblioteca e assim por diante) e o nome do assembly. Será necessário modificar uma ou ambas as propriedades para definir o nome do arquivo de saída.  
  
## <a name="example"></a>Exemplo  
 Compile `t.cs` e crie o arquivo de saída `t.exe`, bem como compile `t2.cs` e crie o arquivo de saída de módulo `mymodule.netmodule`:  
  
```console  
csc t.cs -out:mymodule.netmodule -target:module t2.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Assemblies Amigáveis](../../programming-guide/concepts/assemblies-gac/friend-assemblies.md)  
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
