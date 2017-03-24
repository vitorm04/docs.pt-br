---
title: "entrada/saída (Visual Basic) | Documentos do Microsoft"
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
- /out compiler option [Visual Basic]
- -out compiler option [Visual Basic]
- out compiler option [Visual Basic]
ms.assetid: 9f148c15-0909-4cb8-a2db-777f8a8b45ae
caps.latest.revision: 17
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
ms.openlocfilehash: e3eb7af88869e4fb161a12914c02f2bc2f41864e
ms.lasthandoff: 03/13/2017

---
# <a name="out-visual-basic"></a>/out (Visual Basic)
Especifica o nome do arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/out:filename  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`filename`|Necessário. O nome do arquivo de saída que o compilador cria. Se o nome do arquivo contém um espaço, coloque o nome entre aspas ("").|  
  
## <a name="remarks"></a>Comentários  
 Especifique o nome completo e a extensão do arquivo a ser criado. Se você não fizer isso, o arquivo de .exe leva seu nome a partir do arquivo de código-fonte que contém o `Sub Main` procedimento e o arquivo. dll leva seu nome do primeiro arquivo de código-fonte.  
  
 Se você especificar um nome de arquivo sem uma extensão .exe ou. dll, o compilador adiciona automaticamente a extensão para você, dependendo do valor especificado para o `/target` opção de compilador.  
  
|Para configurar /out no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Tenha um projeto selecionado no **Solution Explorer**. No menu **Projeto**, clique em **Propriedades**. Para obter mais informações, consulte [Introdução ao Designer de Projeto](http://msdn.microsoft.com/en-us/898dd854-c98d-430c-ba1b-a913ce3c73d7).<br />2.  Clique o **aplicativo** guia.<br />3.  Modificar o valor de **nome do Assembly** caixa.|  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `T2.vb` e cria o arquivo de saída `T2.exe`.  
  
```  
vbc t2.vb /out:t3.exe  
```  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)   
 [/Target (Visual Basic)](../../../visual-basic/reference/command-line-compiler/target.md)   
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
