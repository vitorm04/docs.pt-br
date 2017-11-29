---
title: /win32icon
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- win32icon compiler option [Visual Basic]
- -win32icon compiler option [Visual Basic]
- /win32icon compiler option [Visual Basic]
ms.assetid: aecaab01-9353-46c5-941c-6edabd4eff92
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 65149c617220966bc3bb6897d757a71cd60167d6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 11/21/2017
---
# <a name="win32icon"></a>/win32icon
Insere um arquivo. ico no arquivo de saída. Esse arquivo. ico representa o arquivo de saída em **Explorador de arquivos**.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/win32icon:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`filename`|O arquivo. ico para adicionar ao seu arquivo de saída. Coloque o nome do arquivo entre aspas ("") se ele contiver um espaço.|  
  
## <a name="remarks"></a>Comentários  
 Você pode criar um arquivo. ico com o compilador de recurso do Microsoft Windows (RC). O compilador de recurso é chamado quando você compila um programa do Visual C++; é criado um arquivo. ico do arquivo. rc. O `/win32icon` e `/win32resource` são mutuamente exclusivas.  
  
 Consulte [/linkresource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/linkresource.md) a referência de um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recurso, ou [/resource (Visual Basic)](../../../visual-basic/reference/command-line-compiler/resource.md) para anexar um [!INCLUDE[dnprdnshort](~/includes/dnprdnshort-md.md)] arquivo de recurso. Consulte [/win32resource](../../../visual-basic/reference/command-line-compiler/win32resource.md) para importar um arquivo. res.  
  
|Para definir /win32icon no IDE do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique na guia **Aplicativo**.<br />3.  Modificar o valor de **ícone** caixa.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `In.vb` e anexa um arquivo. ico, `Rf.ico`.  
  
```  
vbc /win32icon:rf.ico in.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
