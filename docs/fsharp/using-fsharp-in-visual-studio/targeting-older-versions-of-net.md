---
title: Direcionando o .NET Framework 2.0 no Windows 8
description: 'Saiba mais sobre direcionando a versão mais antiga do .NET Framework ao usar o F #.'
ms.date: 05/16/2016
ms.openlocfilehash: 9b08cced63b46778a5081d4de710991a6299fd29
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="targeting-older-versions-of-net"></a>Direcionamento de versões mais antigas do .NET

> [!NOTE]
Este artigo não é atualizado com o mais recente do Visual Studio.  Ele será atualizado.

O seguinte erro pode aparecer se você tentar direcionar o .NET Framework 2.0, 3.0 ou 3.5 em F # projeto quando o Visual Studio está instalado no Windows 8.1: 

```
This project requires the 2.0 F# runtime, but that runtime is not installed.
```

Esse erro costuma ocorrer sob a seguinte combinação de condições:


- Você instalou o Visual Studio Windows 8.1.
<br />

- Você não habilitar o .NET Framework 3.5 antes de instalar o Visual Studio.
<br />

- Seu projeto direcionado ao .NET Framework 2.0, 3.0 ou 3.5.
<br />

Quando você instala o Visual Studio, ele detecta as versões instaladas do .NET Framework e instala o tempo de execução 2.0 F # somente se o .NET Framework 3.5 está instalado e habilitado.


## <a name="resolving-the-error"></a>Resolver o erro
Para resolver esse erro, você pode ou uma versão mais recente do .NET Framework de destino, ou você pode habilitar o .NET Framework 3.5 no Windows 8.1 e, em seguida, instalar o runtime do F # 2.0 executando o programa de instalação do Visual Studio com o **reparo** opção.


#### <a name="to-enable-the-net-framework-35-on-windows-81"></a>Para habilitar o .NET Framework 3.5 no Windows 8.1

1. Sobre o **iniciar** tela, comece a digitar **painel de controle**.
<br />  Quando você insere esse nome, o **painel de controle** aparece sob o **aplicativos** título.
<br />

2. Escolha o **painel de controle** ícone, escolha o **programas** ícone e, em seguida, escolha o **ativar recursos do Windows ou desativar** link.
<br />

3. Verifique se o **.NET Framework 3.5 (inclui .NET 2.0 e 3.0)** caixa de seleção está selecionada e, em seguida, escolha o **Okey** botão.
<br />  Você não precisa selecionar as caixas de seleção para todos os nós filho para os componentes opcionais do .NET Framework.
<br />  O .NET Framework 3.5 está habilitada, se já não.
<br />


#### <a name="to-install-the-f-20-runtime"></a>Para instalar o tempo de execução do F # 2.0

1. No painel de controle, escolha o **programas** link e, em seguida, escolha o **programas e recursos** link.
<br />

2. Na lista de programas instalados, selecione a edição do Visual Studio que você instalou e, em seguida, escolha o **alteração** botão.
<br />

3. Depois de inicia a instalação, escolha o **reparo** botão.
<br />  Para obter mais informações, consulte [instalar o Visual Studio](https://msdn.microsoft.com/library/e2h7fzkw.aspx).
<br />
## <a name="see-also"></a>Consulte também
[Visual F#](../index.md)
