# package.json

https://classic.yarnpkg.com/lang/en/docs/selective-version-resolutions/

## package.json - resolutions 

  - Yarn은 선택적 버전 확인을 지원하므로, package.json 파일의 resolutions 필드를 통해 종속성 내에서 사용자 지정 패키지 버전 또는 범위를 정의할 수 있음 

### Why? 

- 중요한 업그레이드를 받은 다른 패키지에 의존하는 자주 업데이트되지 않는 패키지에 의존하고 있을 수 있음 

- 이 경우, 직접 종속성에서 지정한 버전 범위가 새 하위 종속성 버전을 포함하지 않으면 작성자를 기다리게 됨 

- 프로젝트 하위 종속성이 중요한 보안 업데이트를 받았고, 직접 종속성이 최소 버전 업데이트를 발행할 때까지 기다리기를 원하지 않음 

- 유지 관리되지는 않지만 작동하는 패키지에 의존하고 있으며, 해당 종속성 중 하나가 업그레이드 되었음 

  - 업그레이드가 문제를 일으키지 않는다는 것을 알고 있으며 단지 사소한 종속성을 업데이트하기 위해 의존하고 있는 패키지를 fork하고 싶지도 않음 

- 종속성은 광범위한 버전 범위를 정의하고 하위 종속성은 방금 문제가 있는 업데이트를 받았으므로 이전 버전에 고정하려고 함 

### 사용하는 방법 

- `package.json` 파일에 `resolutions` 필드를 정의하고, 버전을 오버라이드 해줍니다 

```json
{
  "name": "project",
  "version": "1.0.0",
  "dependencies": {
    "left-pad": "1.0.0",
    "c": "file:../c-1",
    "d2": "file:../d2-1"
  },
  "resolutions": {
    "d2/left-pad": "1.1.1",
    "c/**/left-pad": "^1.1.2"
  }
}
```

- 그 후, `yarn install`을 실행 

### Tip & Trick

- 유효하지 않은 resolution을 정의하는 경우 

  - 유효하지 않은 패키지 이름 사용 예

  - 경고를 받게 됨 

- resolution 버전 또는 범위가 유효하지 않은 경우 경고를 받게 됨 

- resolution 버전 또는 범위가 원래 버전 범위와 호환되지 않는 경우 경고를 받게 됨 

### 제한 사항 및 주의 사항 

- 중첩된 패키지가 제대로 작동하지 않을 수 있음 

- 상당히 새로운 기능이므로 특정 엣지 케이스가 제대로 작동하지 않을 수 있음 