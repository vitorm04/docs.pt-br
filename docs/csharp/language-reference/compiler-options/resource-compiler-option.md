---
title: "-resource (opções do compilador C#)"
ms.date: 07/20/2015
ms.prod: .net
ms.technology: devlang-csharp
ms.topic: article
f1_keywords: /resource
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: "16"
author: BillWagner
ms.author: wiwagn
ms.openlocfilehash: c20de499ae0fd5f8869c9b6e78a308fde9787ef9
ms.sourcegitcommit: c0dd436f6f8f44dc80dc43b07f6841a00b74b23f
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 01/19/2018
---
# <a name="-resource-c-compiler-options"></a>-resource (opções do compilador C#)
Insere o recurso especificado no arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-resource:filename[,identifier[,accessibility-modifier]]  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 O arquivo de recurso do .NET Framework que você deseja inserir no arquivo de saída.  
  
 `identifier` (opcional)  
 O nome lógico do recurso; o nome usado para carregar o recurso. O padrão é o nome do nome de arquivo.  
  
 `accessibility-modifier` (opcional)  
 A acessibilidade do recurso: público ou privado. O padrão é público.  
  
## <a name="remarks"></a>Comentários  
 Use [/linkresource](../../../csharp/language-reference/compiler-options/linkresource-compiler-option.md) para vincular um recurso a um assembly não adicionar o arquivo de recurso ao arquivo de saída.  
  
 Por padrão, recursos são públicos no assembly quando são criados usando o compilador C#. Para tornar os recursos privados, especifique `private` como o modificador de acessibilidade. Não é permitida nenhuma outra acessibilidade diferente de `public` ou `private`.  
  
 Se `filename` for um arquivo de recurso do .NET Framework criado, por exemplo, por [Resgen.exe](../../../framework/tools/resgen-exe-resource-file-generator.md) ou no ambiente de desenvolvimento, ele poderá ser acessado com membros no namespace <xref:System.Resources>. Para obter mais informações, consulte <xref:System.Resources.ResourceManager?displayProperty=nameWithType>. Para todos os outros recursos, use os métodos `GetManifestResource` na classe <xref:System.Reflection.Assembly> para acessar o recurso em tempo de execução.  
  
 **-res** é a forma abreviada de **-resource**.  
  
 A ordem dos recursos no arquivo de saída é determinada com base na ordem especificada na linha de comando.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Adicionar um arquivo de recurso ao seu projeto.  
  
2.  Selecione o arquivo que você deseja inserir no **Gerenciador de Soluções**.  
  
3.  Selecione **Ação de Build** para o arquivo na janela **Propriedades**.  
  
4.  Defina **Ação de Build** como **Recurso inserido**.  
  
 Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.FileProperties2.BuildAction%2A>.  
  
## <a name="example"></a>Exemplo  
 Compile `in.cs` e anexe ao arquivo de recurso `rf.resource`:  
  
```console  
csc -resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)  
 [Gerenciando propriedades de solução e de projeto](/visualstudio/ide/managing-project-and-solution-properties)
