---
title: /filealign | Documentos do Microsoft
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
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
caps.latest.revision: 14
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
ms.openlocfilehash: 18d5c3e327e2e41f4786eda6c3e981125f87389d
ms.lasthandoff: 03/13/2017

---
# <a name="filealign"></a>/filealign
Especifica onde a alinhar as seções do arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
/filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Necessário. Um valor que especifica o alinhamento das seções no arquivo de saída. Os valores válidos são 512, 1024, 2048, 4096 e 8192. Esses valores são em bytes.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o `/filealign` opção para especificar o alinhamento das seções em seu arquivo de saída. Seções são blocos de memória contígua em um arquivo executável portátil (PE) que contém código ou dados. O `/filealign` opção permite que você compilar seu aplicativo com um alinhamento padrão; a maioria dos desenvolvedores não precisam usar essa opção.  
  
 Cada seção é alinhada em um limite que é um múltiplo do `/filealign` valor. Não há nenhum padrão fixo. Se `/filealign` não for especificado, o compilador escolherá um padrão em tempo de compilação.  
  
 Especificando o tamanho da seção, você pode alterar o tamanho do arquivo de saída. Modificando o tamanho da seção pode ser útil para programas que serão executados em dispositivos menores.  
  
> [!NOTE]
>  O `/filealign` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível apenas quando se compila da linha de comando.  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
