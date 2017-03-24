---
title: /win32resource | Documentos do Microsoft
ms.date: 2015-07-20
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- /win32resource
- win32resource
dev_langs:
- VB
helpviewer_keywords:
- /win32resource compiler option [Visual Basic]
- -win32resource compiler option [Visual Basic]
- win32resource compiler option [Visual Basic]
ms.assetid: e226946d-19ce-4cc9-91f5-aed24f77aa2b
caps.latest.revision: 13
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
ms.openlocfilehash: 37902590d5a05d7fdb2a521f3c3de2ad88c2c502
ms.lasthandoff: 03/13/2017

---
# <a name="win32resource"></a>/win32resource
Insere um arquivo de recurso Win32 no arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/win32resource:filename  
```  
  
## <a name="arguments"></a>Arguments  
 `filename`  
 O nome do arquivo de recurso para adicionar ao seu arquivo de saída. Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.  
  
## <a name="remarks"></a>Comentários  
 Você pode criar um arquivo de recurso Win32 com o compilador de recursos do Microsoft Windows (RC).  
  
 Um recurso do Win32 pode conter a versão ou informações de bitmap (ícone) que ajudam a identificar seu aplicativo em **File Explorer**. Se você não especificar `/win32resource`, o compilador gera informações de versão com base na versão do assembly. O `/win32resource` e `/win32icon` são mutuamente exclusivas.  
  
 Consulte [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) a referência de um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] arquivo de recurso, ou [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) para anexar um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] arquivo de recurso.  
  
> [!NOTE]
>  O `/win32resource` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `In.vb` e anexa um arquivo de recurso Win32, `Rf.res`:  
  
```  
vbc /win32resource:rf.res in.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
