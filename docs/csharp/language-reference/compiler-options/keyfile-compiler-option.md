---
title: "-keyfile (Opções do compilador C#) | Microsoft Docs"
ms.date: 2015-07-20
ms.prod: .net
ms.technology:
- devlang-csharp
ms.topic: article
f1_keywords:
- /keyfile
dev_langs:
- CSharp
helpviewer_keywords:
- /keyfile compiler option [C#]
- -keyfile compiler option [C#]
- keyfile compiler option [C#]
ms.assetid: 0815f9de-ace4-4e98-b4c6-13c55dea40c2
caps.latest.revision: 15
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
ms.sourcegitcommit: fe32676f0e39ed109a68f39584cf41aec5f5ce90
ms.openlocfilehash: 4f9ccbfe7126aac3214ccf08015353eec0490cd4
ms.contentlocale: pt-br
ms.lasthandoff: 05/10/2017

---
# <a name="keyfile-c-compiler-options"></a>/keyfile (opções do compilador C#)
Especifica o nome de arquivo que contém a chave de criptografia.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
/keyfile:file  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|----------|----------------|  
|`file`|O nome do arquivo que contém a chave de nome forte.|  
  
## <a name="remarks"></a>Comentários  
 Quando esta opção é usada, o compilador insere a chave pública da linha especificada no manifesto do assembly e, em seguida, assina o assembly definitivo com a chave privada. Para gerar um arquivo de chave, digite sn -k `file` na linha de comando.  
  
 Se você compilar com **/target:module**, o nome do arquivo de chave será mantido no módulo e incorporado no assembly, criado quando você compilar um assembly com [/addmodule](../../../csharp/language-reference/compiler-options/addmodule-compiler-option.md).  
  
 Também é possível passar suas informações de criptografia para o compilador com [/keycontainer](../../../csharp/language-reference/compiler-options/keycontainer-compiler-option.md). Use [/delaysign](../../../csharp/language-reference/compiler-options/delaysign-compiler-option.md) se quiser um assembly parcialmente assinado.  
  
 Caso /keyfile e /keycontainer sejam especificados (pela opção de linha de comando ou pelo atributo personalizado) na mesma compilação, o compilador tentará primeiro o contêiner de chaves. Se isso ocorrer, o assembly será assinado com as informações no contêiner de chaves. Se o compilador não localizar o contêiner de chaves, ele tentará o arquivo especificado com /keyfile. Se isso ocorrer, o assembly será assinado com as informações no arquivo de chave e as informações da chave serão instaladas no contêiner de chaves (semelhante a sn -i), de forma que, na próxima compilação, o contêiner de chaves será válido.  
  
 Observe que um arquivo de chave pode conter somente a chave pública.  
  
 Para obter mais informações, consulte [Criando e usando assemblies de nomes fortes](https://msdn.microsoft.com/library/xwb8f617) e [Atraso na Assinatura de um Assembly](../../../framework/app-domains/delay-sign-assembly.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Para definir esta opção do compilador no ambiente de desenvolvimento do Visual Studio  
  
1.  Abra a página **Propriedades** do projeto.  
  
2.  Clique na página de propriedades **Assinatura**.  
  
3.  Modifique a propriedade **Escolha um arquivo de chave de nome forte**.  
  
 Você pode acessar programaticamente essa opção do compilador com <xref:VSLangProj.ProjectProperties.AssemblyOriginatorKeyFile%2A>.  
  
## <a name="see-also"></a>Consulte também  
 [Opções do compilador do C#](../../../csharp/language-reference/compiler-options/index.md)   
 [NIB: como modificar as propriedades do projeto e as definições de configuração](http://msdn.microsoft.com/en-us/e7184bc5-2f2b-4b4f-aa9a-3ecfcbc48b67)
