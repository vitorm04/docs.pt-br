---
title: -linkresource (opções do compilador C#)
ms.date: 07/20/2015
f1_keywords:
- /linkresource
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
ms.openlocfilehash: feca4713fe0e704799e2abbae3818edd0f3a5c84
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/02/2018
ms.locfileid: "43407731"
---
# <a name="-linkresource-c-compiler-options"></a>-linkresource (opções do compilador C#)
Cria um link para um recurso do .NET Framework no arquivo de saída. O arquivo de recurso não é adicionado ao arquivo de saída. Isso é diferente da opção [-resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) que insere um arquivo de recurso no arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-linkresource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 O arquivo de recurso do .NET Framework ao qual você deseja vincular do assembly.  
  
 `identifier` (opcional)  
 O nome lógico do recurso; o nome usado para carregar o recurso. O padrão é o nome do arquivo.  
  
 `accessibility-modifier` (opcional)  
 A acessibilidade do recurso: público ou privado. O padrão é público.  
  
## <a name="remarks"></a>Comentários  
 Por padrão, os recursos vinculados são públicos no assembly quando são criados usando o compilador C#. Para tornar os recursos privados, especifique `private` como o modificador de acessibilidade. Não é permitido nenhum outro modificador diferente de `public` ou de `private`.  
  
 **-linkresource** requer uma das opções [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) diferentes de **-target:module**.  
  
 Se `filename` for um arquivo de recurso do .NET Framework criado, por exemplo, por [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) ou no ambiente de desenvolvimento, ele poderá ser acessado com membros no namespace <xref:System.Resources>. Para obter mais informações, consulte <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Para todos os outros recursos, use os métodos `GetManifestResource` na classe <xref:System.Reflection.Assembly> para acessar o recurso em tempo de execução.  
  
 O arquivo especificado em `filename` pode ter qualquer formato. Por exemplo, crie uma parte DLL nativa do assembly de maneira que possa ser instalada no cache de assembly global e acessado no código gerenciado no assembly. O segundo dos exemplos a seguir mostra como fazer isso. É possível fazer a mesma coisa no Assembly Linker. O terceiro dos exemplos a seguir mostra como fazer isso. Para obter mais informações, consulte [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md) e [Trabalhando com assemblies e o cache de assembly global](../../../framework/app-domains/working-with-assemblies-and-the-gac.md).  
  
 **-linkres** é a forma abreviada de **-linkresource**.  
  
 Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.  
  
## <a name="example"></a>Exemplo  
 Compile `in.cs` e vincule ao arquivo de recurso `rf.resource`:  
  
```console  
csc -linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Exemplo  
 Compile `A.cs` em uma DLL, vincule a um DLL N.dll nativo e coloque a saída no GAC (Cache de Assembly Global). Nesse exemplo, tanto A.dll quanto N.dll residirão no GAC.  
  
```console  
csc -linkresource:N.dll -t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo faz a mesma coisa que o anterior, mas usando as opções do Assembly Linker.  
  
```console  
csc -t:module A.cs  
al -out:A.dll A.netmodule -link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>Consulte também  

- [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)  
- [Al.exe (Assembly Linker)](../../../framework/tools/al-exe-assembly-linker.md)  
- [Como trabalhar com assemblies e o cache de assembly global](../../../framework/app-domains/working-with-assemblies-and-the-gac.md)  
- [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
