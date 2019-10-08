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
ms.openlocfilehash: fef2652f591e713140c651a9cb0df1ea9e6236c8
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 10/07/2019
ms.locfileid: "72005591"
---
# <a name="-filealign"></a>-filealign
Especifica onde alinhar as seções do arquivo de saída.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-filealign:number  
```  
  
## <a name="arguments"></a>Argumentos  
 `number`  
 Necessário. Um valor que especifica o alinhamento das seções no arquivo de saída. Os valores válidos são 512, 1024, 2048, 4096 e 8192. Esses valores estão em bytes.  
  
## <a name="remarks"></a>Comentários  
 Você pode usar a opção `-filealign` para especificar o alinhamento das seções no arquivo de saída. As seções são blocos de memória contígua em um arquivo executável portátil (PE) que contém o código ou os dados. A opção `-filealign` permite compilar seu aplicativo com um alinhamento não padrão; a maioria dos desenvolvedores não precisa usar essa opção.  
  
 Cada seção é alinhada em um limite que é um múltiplo do valor `-filealign`. Não há nenhum padrão fixo. Se `-filealign` não for especificado, o compilador escolherá um padrão no momento da compilação.  
  
 Ao especificar o tamanho da seção, você pode alterar o tamanho do arquivo de saída. Modificar o tamanho da seção pode ser útil para programas que serão executados em dispositivos menores.  
  
> [!NOTE]
> A opção `-filealign` não está disponível no ambiente de desenvolvimento do Visual Studio; Ele está disponível somente durante a compilação na linha de comando.  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
