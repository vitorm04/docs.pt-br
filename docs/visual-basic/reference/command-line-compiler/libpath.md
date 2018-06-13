---
title: -libpath
ms.date: 03/10/2018
helpviewer_keywords:
- libpath compiler option [Visual Basic]
- /libpath compiler option [Visual Basic]
- -libpath compiler option [Visual Basic]
ms.assetid: 5f1c26c9-3455-4e89-bdf3-b12d6c2e655b
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: a5044bc0093960fdf6b063450d8d3a57575ff07c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33653872"
---
# <a name="-libpath"></a>-libpath
Especifica o local dos assemblies referenciados.  
  
## <a name="syntax"></a>Sintaxe  
  
```  
-libpath:dirList  
```  
  
## <a name="arguments"></a>Arguments  
  
|Termo|Definição|  
|---|---|  
|`dirList`|Necessário. Lista separada por ponto-e-vírgula de diretórios para o compilador ver se um assembly referenciado não foi encontrada no diretório de trabalho atual (o diretório do qual você está chamando o compilador) ou o diretório do sistema do common language runtime. Se o nome do diretório contém um espaço, coloque o nome entre aspas ("").|  
  
## <a name="remarks"></a>Comentários  
 O `-libpath` opção especifica o local dos assemblies referenciados pelo [-referência](../../../visual-basic/reference/command-line-compiler/reference.md) opção.  
  
 O compilador pesquisa referências de assembly que não são totalmente qualificadas na seguinte ordem:  
  
1.  Diretório de trabalho atual. Esse é o diretório do qual o compilador é invocado.  
  
2.  O diretório de sistema do Common Language Runtime.  
  
3.  Diretórios especificados pelo `/libpath`.  
  
4.  Diretórios especificados pela variável de ambiente LIB.  
  
 O `-libpath` opção é aditivas; especificando-mais de uma vez acrescenta a valores anteriores.  
  
 Use `-reference` para especificar uma referência de assembly.  
  
|Configurar /libpath no Visual Studio ambiente de desenvolvimento integrado|  
|---|  
|1.  Selecione um projeto no **Gerenciador de Soluções**. No menu **Projeto**, clique em **Propriedades**. <br />2.  Clique na guia **Referências**.<br />3.  Clique o **caminhos de referência...**  botão.<br />4.  No **caminhos de referência** caixa de diálogo, digite o nome do diretório no **pasta:** caixa.<br />5.  Clique em **adicionar pasta**.|  
  
## <a name="example"></a>Exemplo  
 O código a seguir compila `T2.vb` para criar um arquivo .exe. O compilador procura no diretório de trabalho, no diretório raiz da unidade c: e no diretório da unidade c: novos Assemblies referências de assembly.  
  
```console  
vbc -libpath:c:\;"c:\New Assemblies" -reference:t2.dll t2.vb  
```  
  
## <a name="see-also"></a>Consulte também  
 [Assemblies e o Cache de Assembly Global](../../../visual-basic/programming-guide/concepts/assemblies-gac/index.md)  
 [Compilador de linha de comando do Visual Basic](../../../visual-basic/reference/command-line-compiler/index.md)  
 [Linhas de Comando de Compilação de Exemplo](../../../visual-basic/reference/command-line-compiler/sample-compilation-command-lines.md)
