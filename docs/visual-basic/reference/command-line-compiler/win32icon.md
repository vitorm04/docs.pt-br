---
title: /win32icon | Documentos do Microsoft
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
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: 13
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
ms.openlocfilehash: 110a3861d6628dc2c3fb251aaa31762fb94f04c9
ms.lasthandoff: 03/13/2017

---
# <a name="win32icon"></a>/win32icon
Insere um arquivo. ico no arquivo de saída. Esse arquivo. ico representa o arquivo de saída na **File Explorer**.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/win32icon:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`filename`|O arquivo. ico para adicionar ao seu arquivo de saída. Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.|  
  
## <a name="remarks"></a>Comentários  
 Você pode criar um arquivo. ico com o compilador de recursos do Microsoft Windows (RC). O compilador de recurso é chamado quando você compila um programa do Visual C++; é criado um arquivo. ico no arquivo. rc. O `/win32icon` e `/win32resource` são mutuamente exclusivas.  
  
 Consulte [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) a referência de um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] arquivo de recurso, ou [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) para anexar um [!INCLUDE[dnprdnshort](../../../csharp/getting-started/includes/dnprdnshort_md.md)] arquivo de recurso. Consulte [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) para importar um arquivo. res.  
  
|Definir /win32icon no IDE do Visual Studio|  
|---|  
|1.  Tenha um projeto selecionado no **Solution Explorer**. No menu **Projeto**, clique em **Propriedades**. Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique o **aplicativo** guia.<br />3.  Modificar o valor de **ícone** caixa.|  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `In.vb` e anexa um arquivo. ico, `Rf.ico`.  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
