---
title: -filealign
ms.date: 03/10/2018
helpviewer_keywords:
- sections compiler option [Visual Basic]
- alignment compiler option [Visual Basic]
- -filealign compiler option [Visual Basic]
- section alignment
- /filealign compiler option [Visual Basic]
- filealign compiler option [Visual Basic]
ms.assetid: cc61ec3d-ad38-4b28-9659-099d73cad099
ms.openlocfilehash: 9a844515a4596064937762ac05b850463f1b5e14
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62051696"
---
# <a name="-filealign"></a>-filealign
Especifica onde alinhar as seções do arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-filealign:number  
```  
  
## <a name="arguments"></a>Arguments  
 `number`  
 Necessário. Um valor que especifica o alinhamento das seções no arquivo de saída. Os valores válidos são 512, 1024, 2048, 4096 e 8192. Esses valores estão em bytes.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar o `-filealign` opção para especificar o alinhamento das seções em seu arquivo de saída. As seções são blocos de memória contígua em um arquivo PE (executável portátil) que contém o código ou dados. O `-filealign` opção permite que você compilar seu aplicativo com um alinhamento não padrão; a maioria dos desenvolvedores não precisam usar essa opção.  
  
 Cada seção será alinhada em um limite que é um múltiplo do `-filealign` valor. Não há nenhum padrão fixo. Se `-filealign` não for especificado, o compilador escolhe um padrão em tempo de compilação.  
  
 Especificando o tamanho da seção, você pode alterar o tamanho do arquivo de saída. Modificar o tamanho da seção pode ser útil para programas que serão executados em dispositivos menores.  
  
> [!NOTE]
>  O `-filealign` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ele está disponível somente durante a compilação da linha de comando.  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
