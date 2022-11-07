# ClassToIni

## 사용법

```c#
//base class를 ClassToIni
public class Test : ClassToIni
{
    //세션 네임을 지정가능 기본은 클레스 이름
    [SectionName("Base")]
    public int Test1 { get; set; } = 0; //기본값
    public string Test2 { get; set; } = ""; //기본값

    /// <summary>
    /// 사용하지 않음
    /// </summary>
    [UseINI(false)]
    public string NotUse { get; set; } = "";

    public Test(FileInfo fileInfo) : base(fileInfo)
    {
    }
}

internal class Program
{
    private static void Main(string[] args)
    {
        // 경로지정
        var ini = new Test(new FileInfo(Environment.GetFolderPath(Environment.SpecialFolder.MyDocuments) + "test.ini"));
        // 로드
        ini.LoadINI();
        // 로드한 값 확인
        Console.WriteLine(ini.Test1);
        Console.WriteLine(ini.Test2);
        // 저장할값
        ini.Test1 = 10;
        ini.Test2 = "test";
        // 세이브
        ini.SaveINI();
    }
}
```

