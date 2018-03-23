---
title: -/filealign
ms.date: 03/10/2018
ms.prod: .net
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 26ff29f00f00d3ea5dbbd0bbf01df4d7858771d0
ms.sourcegitcommit: 498799639937c89de777361aab74261efe7b79ea
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 03/22/2018
---
# <a name="-filealign"></a>-/filealign
Especifica onde a alinhar as seções do arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Necessário. Um valor que especifica o alinhamento das seções no arquivo de saída. Os valores válidos são 512, 1024, 2048, 4096 e 8192. Esses valores estão em bytes.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o `-filealign` opção para especificar o alinhamento das seções em seu arquivo de saída. Seções são blocos de memória contígua em um arquivo PE (executável portátil) que contém códigos ou dados. O `-filealign` opção permite que você compilar o aplicativo com um alinhamento padrão; a maioria dos desenvolvedores não precisa usar essa opção.  
  
 Cada seção está alinhada em um limite que é um múltiplo do `-filealign` valor. Não há nenhum padrão fixo. Se `-filealign` não for especificado, o compilador escolhe um padrão em tempo de compilação.  
  
 Especificando o tamanho da seção, você pode alterar o tamanho do arquivo de saída. Modificar o tamanho da seção pode ser útil para programas que serão executados em dispositivos menores.  
  
> [!NOTE]
>  O `-filealign` opção não está disponível no ambiente de desenvolvimento do Visual Studio; está disponível somente quando estiver compilando na linha de comando.  
  
## <a name="see-also"></a>Consulte também  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
