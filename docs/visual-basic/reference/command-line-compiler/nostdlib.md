---
title: /nostdlib (Visual Basic) | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
dev_langs:
- VB
helpviewer_keywords:
- nostdlib compiler option [Visual Basic]
- -nostdlib compiler option [Visual Basic]
- /nostdlib compiler option [Visual Basic]
ms.assetid: 140381b8-dc96-4ad5-ae11-792c9ed0be4d
caps.latest.revision: 18
author: dotnet-bot
ms.author: dotnetcontent
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
translationtype: Machine Translation
ms.sourcegitcommit: a06bd2a17f1d6c7308fa6337c866c1ca2e7281c0
ms.openlocfilehash: 3bacd7d51d12ec6c48dc11ff4b83d842a9e78a30
ms.lasthandoff: 03/13/2017

---
# <a name="nostdlib-visual-basic"></a>/nostdlib (Visual Basic)
Faz com que o compilador não referencie automaticamente as bibliotecas padrão.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/nostdlib  
```  
  
## <a name="remarks"></a>Comentários  
 O `/nostdlib` opção remove a referência automática para o assembly System. dll e impede que o compilador lendo o arquivo Vbc. rsp. O arquivo Vbc. rsp — que está localizado no mesmo diretório que o arquivo Vbc.exe — referencia comumente usados [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies e importa o `System` e `Microsoft.VisualBasic` namespaces.  
  
> [!NOTE]
>  Os assemblies mscorlib. dll e Microsoft.VisualBasic.dll são sempre referenciados.  
  
> [!NOTE]
>  O `/nostdlib` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `T2.vb` sem fazer referência às bibliotecas padrão. Você deve definir o `_MYTYPE` constante de compilação condicional para a cadeia de caracteres "Vazio" para remover o `My` objeto.  
  
```  
vbc /nostdlib /define:_MYTYPE=\"Empty\" T2.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [/noconfig](../../../visual-basic/reference/command-line-compiler/noconfig.md)   
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Exemplos de linhas de comando de compilação](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)   
 [Personalizando quais objetos estão disponíveis em My](../../../visual-basic/developing-apps/customizing-extending-my/customizing-which-objects-are-available-in-my.md)
