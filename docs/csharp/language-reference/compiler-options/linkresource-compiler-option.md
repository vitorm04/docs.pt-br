---
title: "-linkresource (Opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /linkresource
dev_langs:
- CSharp
helpviewer_keywords:
- /linkresource compiler option [C#]
- linkres compiler option [C#]
- /linkres compiler option [C#]
- -linkres compiler option [C#]
- -linkresource compiler option [C#]
- linkresource compiler option [C#]
ms.assetid: 440c26c2-77c1-4811-a0a3-57cce3f5fc96
caps.latest.revision: 17
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
ms.openlocfilehash: 29bff90e24c01502e3a1761f1cc1d41299c97b72
ms.lasthandoff: 03/13/2017

---
# <a name="linkresource-c-compiler-options"></a>/linkresource (opções do compilador C#)
Cria um link para um recurso do .NET Framework no arquivo de saída. O arquivo de recurso não é adicionado ao arquivo de saída. Isso é diferente da opção [/resource](../../../csharp/language-reference/compiler-options/resource-compiler-option.md) que insere um arquivo de recurso no arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/linkresource:filename[,identifier[,accessibility-modifier]]  
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
  
 **/linkresource** requer uma das opções [/target](../../../csharp/language-reference/compiler-options/target-compiler-option.md) diferentes de **/target:module**.  
  
 Se `filename` for um arquivo de recurso do .NET Framework criado, por exemplo, por [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou no ambiente de desenvolvimento, ele poderá ser acessado com membros no namespace <xref:System.Resources>. Para obter mais informações, consulte <xref:System.Resources.ResourceManager?displayProperty=fullName>. Para todos os outros recursos, use os métodos `GetManifestResource` * na classe <xref:System.Reflection.Assembly> para acessar o recurso no tempo de execução.  
  
 O arquivo especificado em `filename` pode ter qualquer formato. Por exemplo, crie uma parte DLL nativa do assembly de maneira que possa ser instalada no cache de assembly global e acessado no código gerenciado no assembly. O segundo dos exemplos a seguir mostra como fazer isso. É possível fazer a mesma coisa no Assembly Linker. O terceiro dos exemplos a seguir mostra como fazer isso. Para obter mais informações, consulte [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex) e [Trabalhando com assemblies e o cache de assembly global](http://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433).  
  
 **/linkres** é a forma abreviada de **/linkresource**.  
  
 Essa opção do compilador não está disponível no Visual Studio e não pode ser alterada programaticamente.  
  
## <a name="example"></a>Exemplo  
 Compile `in.cs` e vincule ao arquivo de recurso `rf.resource`:  
  
```  
csc /linkresource:rf.resource in.cs  
```  
  
## <a name="example"></a>Exemplo  
 Compile `A.cs` em uma DLL, vincule a um DLL N.dll nativo e coloque a saída no GAC (Cache de Assembly Global). Nesse exemplo, tanto A.dll quanto N.dll residirão no GAC.  
  
```  
csc /linkresource:N.dll /t:library A.cs  
gacutil -i A.dll  
```  
  
## <a name="example"></a>Exemplo  
 Este exemplo faz a mesma coisa que o anterior, mas usando as opções do Assembly Linker.  
  
```  
csc /t:module A.cs  
al /out:A.dll A.netmodule /link:N.dll   
gacutil -i A.dll  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [Al.exe (Assembly Linker)](https://msdn.microsoft.com/library/c405shex)   
 [Trabalhando com assemblies e o cache de assembly global](http://msdn.microsoft.com/library/8a18e5c2-d41d-49ef-abcb-7c27e2469433)   
 [NIB: como modificar as propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
