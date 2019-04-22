---
title: -nowarn
ms.date: 07/20/2015
helpviewer_keywords:
- nowarn compiler option [Visual Basic]
- /nowarn compiler option [Visual Basic]
- -nowarn compiler option [Visual Basic]
ms.assetid: 7ebf2106-0652-4fdc-bf60-70fc86465d83
ms.openlocfilehash: 31f7a2b771cfa1bcc6581d720aa0de3505aec826
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 04/18/2019
ms.locfileid: "58828206"
---
# <a name="-nowarn"></a>-nowarn
Suprime a capacidade do compilador para gerar avisos.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-nowarn[:numberList]  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`numberList`|Opcional. Lista delimitada por vírgula dos números de ID de aviso que o compilador deve eliminar. Se as IDs de aviso não forem especificadas, todos os avisos estão suprimidos.|  
  
## <a name="remarks"></a>Comentários  
 O `-nowarn` opção faz com que o compilador não gere avisos. Para suprimir um aviso individual, forneça a ID do aviso para o `-nowarn` opção após os dois-pontos. Separe vários números de aviso com vírgulas.  
  
 Você precisa especificar somente a parte numérica do identificador de aviso. Por exemplo, se você desejar suprimir BC42024, o aviso para variáveis locais não utilizados, especificar `-nowarn:42024`.  
  
 Para obter mais informações sobre os números de ID do aviso, consulte [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic).  
  
|Definir - nowarn no ambiente de desenvolvimento integrado do Visual Studio|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Compilar**.<br />3.  Selecione o **desabilitar todos os avisos** caixa de seleção para desabilitar todos os avisos.<br />     - ou -<br />     Para desabilitar um aviso específico, clique em **nenhum** na lista suspensa adjacente ao aviso.|  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `T2.vb` e não exibe todos os avisos.  
  
```console
vbc -nowarn t2.vb  
```  
  
## <a name="example"></a>Exemplo  
 O seguinte código compila `T2.vb` e não exibe os avisos para variáveis locais não utilizadas (42024).  
  
```console
vbc -nowarn:42024 t2.vb  
```  
  
## <a name="see-also"></a>Consulte também

- [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)
- [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
- [Configurando avisos no Visual Basic](/visualstudio/ide/configuring-warnings-in-visual-basic)
