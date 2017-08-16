---
title: "-doc (Opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- FileProperties.BuildAction
- /doc
dev_langs:
- CSharp
helpviewer_keywords:
- comments, C# code
- XML documentation [C#], comments in source files
- doc compiler option [C#]
- Visual C#, XML documentation for
- -doc compiler option [C#]
- /doc compiler option [C#]
ms.assetid: 849eea59-c936-4311-bad8-d07404480f2a
caps.latest.revision: 19
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
ms.translationtype: Human Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 8addbbfe1e854feee560192292b713da4fc67e6c
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="doc-c-compiler-options"></a>/doc (opções do compilador C#)
A opção **/doc** permite colocar comentários de documentação em um arquivo XML.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/doc:file  
```  
  
## <a name="arguments"></a>Arguments  
 `file`  
 O arquivo de saída para XML, que é populado com os comentários nos arquivos de código-fonte da compilação.  
  
## <a name="remarks"></a>Comentários  
 Nos arquivos de código-fonte, os comentários de documentação que precedem o seguinte podem ser processados e adicionados ao arquivo XML:  
  
-   Tipos definidos pelo usuário, como [classe](../../../csharp/language-reference/keywords/class.md), [delegado](../../../csharp/language-reference/keywords/delegate.md) ou [interface](../../../csharp/language-reference/keywords/interface.md)  
  
-   Membros como um campo, [evento](../../../csharp/language-reference/keywords/event.md), [propriedade](../../../csharp/programming-guide/classes-and-structs/using-properties.md) ou método  
  
 O arquivo de código-fonte que contém Main é gerado primeiro no XML.  
  
 Para usar o arquivo .xml gerado para uso com o recurso [IntelliSense](https://docs.microsoft.com/visualstudio/ide/using-intellisense), deixe o nome do arquivo .xml igual ao do assembly a que você deseja dar suporte e, em seguida, verifique se o arquivo .xml está no mesmo diretório que o assembly. Sendo assim, quando o assembly for referenciado no projeto do Visual Studio, o arquivo .xml também será encontrado. Consulte [Fornecendo comentários de código](https://docs.microsoft.com/visualstudio/ide/supplying-xml-code-comments) para obter mais informações.  
  
 A menos que você compile com [/target:module](../../../csharp/language-reference/compiler-options/target-module-compiler-option.md), `file` conterá marcas \<assembly>\</assembly> especificando o nome do arquivo que contém o manifesto do assembly para o arquivo de saída da compilação.  
  
> [!NOTE]
>  A opção /doc se aplica a todos os arquivos de entrada ou, se definida nas Configurações do Projeto, todos os arquivos no projeto. Para desabilitar avisos relacionados aos comentários de documentação para um arquivo ou uma seção específica do código, use [#pragma warning](../../../csharp/language-reference/preprocessor-directives/preprocessor-pragma-warning.md).  
  
 Consulte [Marcas recomendadas para comentários de documentação](../../../csharp/programming-guide/xmldoc/recommended-tags-for-documentation-comments.md) para ver maneiras de gerar a documentação dos comentários em seu código.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na guia **Build**.  
  
3.  Modifique a propriedade **Arquivo de documentação XML**.  
  
 Para obter informações sobre como definir essa opção do compilador de maneira programática, consulte <xref:VSLangProj80.CSharpProjectConfigurationProperties3.DocumentationFile%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB: como modificar as propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
