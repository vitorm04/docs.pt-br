---
title: "-resource (Opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /resource
dev_langs:
- CSharp
helpviewer_keywords:
- -resource compiler option [C#]
- /resource compiler option [C#]
- -res compiler option [C#]
- /res compiler option [C#]
- res compiler option [C#]
- resource compiler option [C#]
ms.assetid: 5212666e-98ab-47e4-a497-b5545ab15c7f
caps.latest.revision: 16
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
ms.openlocfilehash: e8c27b8cfca42c6f84dec95824c6611ff5ccc577
ms.contentlocale: pt-br
ms.lasthandoff: 03/13/2017

---
# <a name="resource-c-compiler-options"></a>/resource (opções do compilador C#)
Insere o recurso especificado no arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/resource:filename[,identifier[,accessibility-modifier]]  
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
  
 Se `filename` for um arquivo de recurso do .NET Framework criado, por exemplo, por [Resgen.exe](http://msdn.microsoft.com/library/8ef159de-b660-4bec-9213-c3fbc4d1c6f4) ou no ambiente de desenvolvimento, ele poderá ser acessado com membros no namespace <xref:System.Resources>. Para obter mais informações, consulte <xref:System.Resources.ResourceManager?displayProperty=fullName>. Para todos os outros recursos, use os métodos `GetManifestResource` * na classe <xref:System.Reflection.Assembly> para acessar o recurso no tempo de execução.  
  
 **/res** é a forma abreviada de **/resource**.  
  
 A ordem dos recursos no arquivo de saída é determinada com base na ordem especificada na linha de comando.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Adicionar um arquivo de recurso ao seu projeto.  
  
2.  Selecione o arquivo que você deseja inserir no **Gerenciador de Soluções**.  
  
3.  Selecione **Ação de Build** para o arquivo na janela **Propriedades**.  
  
4.  Defina **Ação de Build** como **Recurso inserido**.  
  
 Para obter informações sobre como definir essa opção do compilador de maneira programática, consulte <xref:VSLangProj80.FileProperties2.BuildAction%2A>.  
  
## <a name="example"></a>Exemplo  
 Compile `in.cs` e anexe ao arquivo de recurso `rf.resource`:  
  
```console  
csc /resource:rf.resource in.cs  
```  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB: como modificar as propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
