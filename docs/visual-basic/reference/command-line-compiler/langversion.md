---
title: -langversion (Visual Basic)
ms.date: 03/10/2018
helpviewer_keywords:
- /langversion compiler option [Visual Basic]
- langversion compiler option [Visual Basic]
- -langversion compiler option [Visual Basic]
ms.assetid: 59b7b0c8-2dde-4e9b-94e7-0237f7e0bafb
ms.openlocfilehash: db2cb1eb107973e9ce60ecb0d669c677d4fa2c51
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58839711"
---
# <a name="-langversion-visual-basic"></a>-langversion (Visual Basic)
Faz com que o compilador aceite somente a sintaxe incluída na versão especificada de linguagem do Visual Basic.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-langversion:version  
```  
  
## <a name="arguments"></a>Arguments  
 `version`  
 Necessário. A versão de idioma a ser usado durante a compilação. Os valores aceitos são `9`, `10`, `11`, `12`, `14`, `15`, `15.3`, `15.5`, `default` e `latest`.

 Qualquer um dos números inteiros também podem ser especificados usando `.0` como a versão secundária, por exemplo, `11.0`.

 Você pode ver a lista de todos os valores possíveis, especificando `-langversion:?` na linha de comando.  
  
## <a name="remarks"></a>Comentários  
 O `-langversion` opção especifica qual sintaxe que o compilador aceita. Por exemplo, se você especificar que a versão de idioma é 9.0, o compilador gera erros de sintaxe que é válido somente na versão 10.0 e posterior.  
  
 Você pode usar essa opção ao desenvolver aplicativos destinados a diferentes versões do .NET Framework. Por exemplo, se estiver direcionando o .NET Framework 3.5, você pode usar essa opção para garantir que você não use a sintaxe da versão 10.0 do idioma.  
  
 Você pode definir `-langversion` diretamente usando a linha de comando. Para obter mais informações, consulte [Definindo uma Versão Específica do .NET Framework como Destino](/visualstudio/ide/targeting-a-specific-dotnet-framework-version).  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `sample.vb` para Visual Basic 9.0.  
  
```console  
vbc -langversion:9.0 sample.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Direcionamento de uma versão específica do .NET Framework](/visualstudio/ide/targeting-a-specific-dotnet-framework-version)
