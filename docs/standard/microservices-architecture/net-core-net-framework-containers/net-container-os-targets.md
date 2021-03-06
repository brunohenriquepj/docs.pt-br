---
title: Para qual sistema operacional direcionar com os contêineres do .NET
description: Arquitetura de microsserviços do .NET para aplicativos .NET em contêineres | Para qual sistema operacional direcionar com os contêineres do .NET
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/18/2017
ms.openlocfilehash: 0b06f64027a736ead148ea5511cf20e900b8b39a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: HT
ms.contentlocale: pt-BR
ms.lasthandoff: 05/04/2018
---
# <a name="what-os-to-target-with-net-containers"></a>Para qual sistema operacional direcionar com os contêineres do .NET

Dada a diversidade de sistemas operacionais compatíveis com o Docker e as diferenças entre o .NET Framework e o .NET Core, você deve direcionar um sistema operacional e versões específicos dependendo da estrutura que você está usando. 

Para o Windows, é possível usar o Windows Server Core ou o Windows Nano Server. Essas versões do Windows oferecem características diferentes (IIS no Windows Server Core versus um servidor Web auto-hospedado como Kestrel no Nano Server) que podem ser exigidas pelo .NET Framework ou pelo .NET Core, respectivamente. 

Para Linux, várias distribuições estão disponíveis e há compatibilidade com elas nas imagens oficiais do .NET Docker (como Debian).

Na Figure 3-1, é possível ver a possível versão do sistema operacional dependendo do .NET Framework usado.

![](./media/image1.png)

**Figura 3-1.** Sistemas operacionais a serem direcionados dependendo das versões do .NET Framework

Também é possível criar sua própria imagem do Docker em casos em que você deseja usar uma distribuição diferente do Linux ou em que você quer uma imagem com versões não fornecidas pela Microsoft. Por exemplo, você pode criar uma imagem com o ASP.NET Core em execução no .NET Framework tradicional e no Windows Server Core, que é um cenário não tão comum para Docker.

Ao adicionar o nome de imagem ao seu arquivo Dockerfile, é possível selecionar o sistema operacional e a versão dependendo da marcação usada, como nos seguintes exemplos:

-   microsoft/**dotnet:2.0.0-runtime-jessie**

        .NET Core 2.0 runtime-only on Linux

-   microsoft/**dotnet:2.0.0-runtime-nanoserver-1709** 

        .NET Core 2.0 runtime-only on Windows Nano Server (Windows Server 2016 Fall Creators Update version 1709)

-   microsoft/**aspnetcore:2.0**
    
        .NET Core 2.0 multi-architecture: Supports Linux and Windows Nano Server depending on the Docker host.
        The aspnetcore image has a few optimizations for ASP.NET Core. 





>[!div class="step-by-step"]
[Anterior] (container-framework-choice-factors.md) [Próximo] (official-net-docker-images.md)
