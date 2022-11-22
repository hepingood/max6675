[English](/README.md) | [ 简体中文](/README_zh-Hans.md) | [繁體中文](/README_zh-Hant.md) | [日本語](/README_ja.md) | [Deutsch](/README_de.md) | [한국어](/README_ko.md)

<div align=center>
<img src="/doc/image/logo.png"/>
</div>

## LibDriver MAX6675

[![MISRA](https://img.shields.io/badge/misra-compliant-brightgreen.svg)](/misra/README.md) [![API](https://img.shields.io/badge/api-reference-blue.svg)](https://www.libdriver.com/docs/max6675/index.html) [![License](https://img.shields.io/badge/license-MIT-brightgreen.svg)](/LICENSE)

MAX6675는 냉접점 보상을 수행하고 K형 열전쌍의 신호를 디지털화합니다. 데이터는 12비트 분해능, SPI 호환, 읽기 전용 형식으로 출력됩니다. 이 변환기는 온도를 0.25°C로 분해하고 최대 +1024°C의 판독을 허용하며 다음 범위의 온도에 대해 8LSB의 열전대 정확도를 나타냅니다. 0°C ~ +700°C. MAX6675는 소형 8핀 SO 패키지로 제공됩니다. 산업용, 가전제품, HVAC 등에 사용할 수 있습니다.

LibDriver MAX6675는 LibDriver에서 출시한 MAX6675의 전체 기능 드라이버입니다. 온도 읽기 기능 등을 제공합니다. LibDriver는 MISRA를 준수합니다.

### 콘텐츠

  - [설명](#설명)
  - [설치](#설치)
  - [사용](#사용)
    - [example basic](#example-basic)
  - [문서](#문서)
  - [기고](#기고)
  - [저작권](#저작권)
  - [문의하기](#문의하기)

### 설명

/src 디렉토리에는 LibDriver MAX6675의 소스 파일이 포함되어 있습니다.

/interface 디렉토리에는 LibDriver MAX6675용 플랫폼 독립적인 SPI버스 템플릿이 포함되어 있습니다.

/test 디렉토리에는 LibDriver MAX6675드라이버 테스트 프로그램이 포함되어 있어 칩의 필요한 기능을 간단히 테스트할 수 있습니다.

/example 디렉토리에는 LibDriver MAX6675프로그래밍 예제가 포함되어 있습니다.

/doc 디렉토리에는 LibDriver MAX6675오프라인 문서가 포함되어 있습니다.

/datasheet 디렉토리에는 MAX6675데이터시트가 있습니다.

/project 디렉토리에는 일반적으로 사용되는 Linux 및 마이크로컨트롤러 개발 보드의 프로젝트 샘플이 포함되어 있습니다. 모든 프로젝트는 디버깅 방법으로 셸 스크립트를 사용하며, 자세한 내용은 각 프로젝트의 README.md를 참조하십시오.

### 설치

/interface 디렉토리에서 플랫폼 독립적인 SPI버스 템플릿을 참조하여 지정된 플랫폼에 대한 SPI버스 드라이버를 완성하십시오.

/src 디렉토리, /interface 디렉토리 및 /example 디렉토리를 프로젝트에 추가하십시오.

### 사용

#### example basic

```C
#include "driver_max6675_basic.h"

uint8_t res;
uint32_t i;
uint32_t times;

times = 3;
res = max6675_basic_init();
if (res != 0)
{
    return 1;
}

...
    
for (i = 0; i < times; i++)
{
    uint16_t raw;
    float temp;

    /* read data */
    res = max6675_basic_read(&raw, &temp);
    if (res != 0)
    {
        (void)max6675_basic_deinit();

        return 1;
    }

    /* output */
    max6675_interface_debug_print("%d/%d %0.2fC.\n", i + 1, times, temp);

    /* delay 1000ms */
    max6675_interface_delay_ms(1000);
    
    ...
}

...
    
/* deinit */
(void)max6675_basic_deinit();

return 0;
```

### 문서

온라인 문서: https://www.libdriver.com/docs/max6675/index.html

오프라인 문서: /doc/html/index.html

### 기고

연락주세요lishifenging@outlook.com

### 저작권

저작권 (c) 2015 - 지금 LibDriver 판권 소유

MIT 라이선스(MIT)

이 소프트웨어 및 관련 문서 파일("소프트웨어")의 사본을 얻은 모든 사람은 이에 따라 무제한 사용, 복제, 수정, 통합, 출판, 배포, 2차 라이선스를 포함하여 소프트웨어를 처분할 수 있는 권리가 부여됩니다. 소프트웨어의 사본에 대한 라이선스 및/또는 판매, 그리고 소프트웨어가 위와 같이 배포된 사람의 권리에 대한 2차 라이선스는 다음 조건에 따릅니다.

위의 저작권 표시 및 이 허가 표시는 이 소프트웨어의 모든 사본 또는 내용에 포함됩니다.

이 소프트웨어는 상품성, 특정 목적에의 적합성 및 비침해에 대한 보증을 포함하되 이에 국한되지 않는 어떠한 종류의 명시적 또는 묵시적 보증 없이 "있는 그대로" 제공됩니다. 어떤 경우에도 저자 또는 저작권 소유자는 계약, 불법 행위 또는 기타 방식에 관계없이 소프트웨어 및 기타 소프트웨어 사용으로 인해 발생하거나 이와 관련하여 발생하는 청구, 손해 또는 기타 책임에 대해 책임을 지지 않습니다.

### 문의하기

연락주세요lishifenging@outlook.com