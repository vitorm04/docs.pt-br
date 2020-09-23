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
ms.openlocfilehash: 809b7ad005b6bb5f127f84425b5d2beb980df471
ms.sourcegitcommit: bf5c5850654187705bc94cc40ebfb62fe346ab02
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/23/2020
ms.locfileid: "91058125"
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

 Você pode usar a `-filealign` opção para especificar o alinhamento das seções no arquivo de saída. As seções são blocos de memória contígua em um arquivo executável portátil (PE) que contém o código ou os dados. A `-filealign` opção permite que você compile seu aplicativo com um alinhamento não padrão; a maioria dos desenvolvedores não precisa usar essa opção.  
  
 Cada seção é alinhada em um limite que é um múltiplo do `-filealign` valor. Não há nenhum padrão fixo. Se `-filealign` não for especificado, o compilador escolherá um padrão no momento da compilação.  
  
 Ao especificar o tamanho da seção, você pode alterar o tamanho do arquivo de saída. Modificar o tamanho da seção pode ser útil para programas que serão executados em dispositivos menores.  
  
> [!NOTE]
> A `-filealign` opção não está disponível no ambiente de desenvolvimento do Visual Studio; ela está disponível somente durante a compilação na linha de comando.  
  
## <a name="see-also"></a>Confira também

- [Compilador de linha de comando do Visual Basic](index.md)
