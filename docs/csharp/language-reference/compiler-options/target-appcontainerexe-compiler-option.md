---
description: -target:appcontainerexe (opções do compilador C#)
title: -target:appcontainerexe (opções do compilador C#)
ms.date: 07/20/2015
ms.assetid: e7e62229-23ea-4e53-bef5-380d951bf95f
ms.openlocfilehash: 8c3b85c2f5a20788bd311e9bf3b300c32967da77
ms.sourcegitcommit: d579fb5e4b46745fd0f1f8874c94c6469ce58604
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 08/30/2020
ms.locfileid: "89128576"
---
# <a name="-targetappcontainerexe-c-compiler-options"></a>-target:appcontainerexe (opções do compilador C#)
Se você usar a opção do compilador **-target:appcontainerexe**, o compilador criará um arquivo executável (.exe) do Windows que deverá ser executado em um contêiner de aplicativos. Essa opção é equivalente a [-target: winexe](./target-winexe-compiler-option.md) , mas é projetada para aplicativos da loja do Windows 8. x.  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-target:appcontainerexe  
```  
  
## <a name="remarks"></a>Comentários  
 Para exigir que o aplicativo seja executado em um contêiner de aplicativos, esta opção define um bit no arquivo [PE](/windows/desktop/Debug/pe-format). Quando esse bit estiver definido, ocorrerá um erro se o método CreateProcess tentar inicializar o arquivo executável fora de um contêiner de aplicativos.  
  
 A menos que você use a opção [-out](./out-compiler-option.md), o nome do arquivo de saída usará o nome do arquivo de entrada que contém o método [Main](../../programming-guide/main-and-command-args/index.md).  
  
 Quando você especifica essa opção em um prompt de comando, todos os arquivos até a próxima opção **-out** ou **-target** são usados para criar o arquivo executável.  
  
### <a name="to-set-this-compiler-option-in-the-ide"></a>Para definir esta opção do compilador no IDE  
  
1. No **Gerenciador de Soluções**, abra o menu de atalho do projeto e escolha **Propriedades**.  
  
2. Na guia **Aplicativo**, na lista **Tipo de saída**, escolha **Aplicativo da Windows Store**.  
  
     Essa opção está disponível somente para modelos de aplicativo da loja do Windows 8. x.  
  
 Para saber mais sobre como definir essa opção do compilador programaticamente, veja <xref:VSLangProj80.ProjectProperties3.OutputType%2A>.  
  
## <a name="example"></a>Exemplo  
 O comando a seguir compila `filename.cs` em um arquivo executável do Windows que pode ser executado somente em um contêiner de aplicativos.  
  
```console  
csc -target:appcontainerexe filename.cs  
```  
  
## <a name="see-also"></a>Confira também

- [-Target (opções do compilador C#)](./target-compiler-option.md)
- [-Target: winexe (opções do compilador C#)](./target-winexe-compiler-option.md)
- [Opções do compilador C#](./index.md)
