---
title: /noconfig | Documentos do Microsoft
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
- noconfig compiler option [Visual Basic]
- -noconfig compiler option [Visual Basic]
- /noconfig compiler option [Visual Basic]
ms.assetid: a7405067-bd21-4171-adf4-a126fa3ad6c3
caps.latest.revision: 15
author: stevehoag
ms.author: shoag
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
ms.openlocfilehash: 304d0e7fc787adb1d7776a2c047090ffc230fcc1
ms.lasthandoff: 03/13/2017

---
# <a name="noconfig"></a>/noconfig
Especifica que o compilador não deve automaticamente referenciar comumente usados [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies ou importar a `System` e `Microsoft.VisualBasic` namespaces.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/noconfig  
```  
  
## <a name="remarks"></a>Comentários  
 O `/noconfig` opção informa o compilador não deve compilar com o arquivo Vbc. exe, que está localizado no mesmo diretório que o arquivo Vbc.exe. O arquivo Vbc. rsp faz referência comumente usados [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] assemblies e importa o `System` e `Microsoft.VisualBasic` namespaces. O compilador implicitamente referencia o assembly System. dll, a menos que o `/nostdlib` opção é especificada. O `/nostdlib` opção informa o compilador não deve compilar com Vbc ou referenciar automaticamente o assembly System. dll.  
  
> [!NOTE]
>  Os assemblies mscorlib. dll e Microsoft.VisualBasic.dll são sempre referenciados.  
  
 Você pode modificar o arquivo Vbc. rsp para especificar opções adicionais do compilador que devem ser incluídas em cada compilação Vbc.exe (exceto quando o `/noconfig` opção). Para obter mais informações, confira [@ (Especificar de arquivo de resposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md).  
  
 O compilador processa as opções passadas para o `vbc` último comando. Portanto, qualquer opção na linha de comando substitui a configuração da mesma opção no arquivo Vbc.  
  
> [!NOTE]
>  O `/noconfig` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.  
  
## <a name="see-also"></a>Consulte também  
 [/nostdlib (Visual Basic)](../../../visual-basic/reference/command-line-compiler/nostdlib.md)   
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [@ (Especificar arquivo de resposta)](../../../visual-basic/reference/command-line-compiler/specify-response-file.md)   
 [/Reference (Visual Basic)](../../../visual-basic/reference/command-line-compiler/reference.md)
