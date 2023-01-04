# Snapshot

로컬에 있는 스토어를 압축하여 제네시스와 스냅샷 팁 블록의 해시에 따라 이름을 정해줍니다. *{genesisHash}-snapshot-{tipHash}.zip*

리오그로 스냅샷이 동작하지 않는 경우를 피하기 위해 기본값으로 10블록 이전의 블록을 팁으로하는
스냅샷을 만들며 `--block-before` 옵션을 통해 몇블록 전의 스냅샷을 찍을지 조정할 수 있습니다.

팁 블록의 헤더 정보와 APV를 별도의 파일로 저장합니다. *{genesisHash}-snapshot-{tipHash}.json*

생성한 스냅샷을 론처 업데이터에서 사용하게 하고 싶다면 *https://9c-test.s3.ap-northeast-2.amazonaws.com/latest/{genesisHash}-snapshot.zip*,
*https://9c-test.s3.ap-northeast-2.amazonaws.com/latest/{genesisHash}-snapshot.json*
경로에 업로드 해야 합니다.

`--snapshot-type` 옵션을 사용하는 경우, default로 증분 스냅샷이 찍힙니다. 옵션 값으로 `full`을 사용하면, 통 스냅샷으로 찍히며 `all`을 사용하면 증분 & 통 스냅샷이 모두 찍힙니다.

```
$ dotnet run -- --help
Usage: Snapshot [--store-path <String>] [--output-directory <String>] [--block-before <Int32>] [--apv <String>] [--snapshot-type <String>] [--help] [--version]

Snapshot

Options:
  --apv <String>                      (Required)
  -o, --output-directory <String>     (Default: )
  --store-path <String>               (Default: )
  --block-before <Int32>              (Default: 10)
  --snapshot-type <String>            (Default: partition)
  -h, --help                         Show help message
  --version                          Show version
```
