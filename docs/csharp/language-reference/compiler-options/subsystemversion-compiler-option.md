---
title: -subsystemversion (opções do compilador C#)
ms.date: 07/20/2015
ms.assetid: a99fce81-9d92-4813-9874-bee777041445
ms.openlocfilehash: ff4cd196edc1ec04f8abcecfa1a7a4e99e32dd56
ms.sourcegitcommit: dfb2a100cfb4d3902c042f17b3204f49bc7635e7
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 09/21/2018
ms.locfileid: "46508837"
---
# <a name="-subsystemversion-c-compiler-options"></a>-subsystemversion (opções do compilador C#)
Especifica a versão mínima do subsistema no qual o arquivo executável gerado pode ser executado, determinando assim as versões do Windows em que o arquivo executável pode ser executado. Normalmente, essa opção garante que o arquivo executável possa tirar proveito de determinados recursos de segurança que não estão disponíveis com versões mais antigas do Windows.  
  
> [!NOTE]
>  Para especificar o subsistema em si, use a opção do compilador [-target](../../../csharp/language-reference/compiler-options/target-compiler-option.md).  
  
## <a name="syntax"></a>Sintaxe  
  
```console  
-subsystemversion:major.minor  
```  
  
#### <a name="parameters"></a>Parâmetros  
 `major.minor`  
 A versão mínima obrigatória do subsistema, conforme expresso em uma notação de ponto para versões principais e secundárias. Por exemplo, você pode especificar que um aplicativo não pode ser executado em um sistema operacional mais antigo que o Windows 7 se definir o valor dessa opção como 6.01, conforme descrito na tabela mais adiante neste tópico. Você deve especificar os valores de `major` e `minor` como inteiros.  
  
 Zeros à esquerda na versão `minor` não alteram a versão, mas zeros à direita alteram. Por exemplo, 6.1 e 6.01 se referem à mesma versão, mas 6.10 se refere a uma versão diferente. É recomendável expressar a versão secundária como dois dígitos para evitar confusão.  
  
## <a name="remarks"></a>Comentários  
 A seguinte tabela lista as versões de subsistema comuns do Windows.  
  
|Versão do Windows|Versão do subsistema|  
|---------------------|-----------------------|  
|Windows 2000|5.00|  
|Windows XP|5.01|  
|Windows Server 2003|5.02|  
|Windows Vista|6.00|  
|Windows 7|6.01|  
|Windows Server 2008|6.01|  
|[!INCLUDE[win8](~/includes/win8-md.md)]|6.02|  
  
## <a name="default-values"></a>Valores padrão  
 O valor padrão da opção do compilador **-subsystemversion** depende das condições na lista a seguir:  
  
-   O valor padrão é 6.02 se qualquer opção do compilador na lista a seguir for definida:  
  
    -   [/target:appcontainerexe](../../../csharp/language-reference/compiler-options/target-appcontainerexe-compiler-option.md)  
  
    -   [/target:winmdobj](../../../csharp/language-reference/compiler-options/target-winmdobj-compiler-option.md)  
  
    -   [-platform:arm](../../../csharp/language-reference/compiler-options/platform-compiler-option.md)  
  
-   O valor padrão é 6.00 se você estiver usando o MSBuild, se tiver como alvo [!INCLUDE[net_v45](~/includes/net-v45-md.md)] e se não tiver definido nenhuma das opções de compilador que foram especificadas anteriormente na lista.  
  
-   O valor padrão é 4.00 se nenhuma das condições anteriores for verdadeira.  
  
## <a name="setting-this-option"></a>Definindo esta opção  
 Para definir a opção do compilador **-subsystemversion** no Visual Studio, você precisa abrir o arquivo .csproj e especificar um valor para a propriedade `SubsystemVersion` no XML do MSBuild. Você não pode definir essa opção no IDE do Visual Studio. Para obter mais informações, consulte "Valores padrão" no início deste tópico ou [Propriedades de projeto comuns do MSBuild](/visualstudio/msbuild/common-msbuild-project-properties).  
  
## <a name="see-also"></a>Consulte também  

- [Opções do compilador de C#](../../../csharp/language-reference/compiler-options/index.md)
