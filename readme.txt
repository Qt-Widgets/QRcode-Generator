QRcode��һ�������������ά���С���������ɺͽ�������QR��ά�루�ձ���һ�ҹ�˾���Ƶľ���ʽ��ά����ţ���QR��Ҳ�ǵ�ǰʹ����㷺�Ķ�ά��֮һ��΢��֧������ɨ�붼��QR�롣

QR�����ż��临�ӵı��뼰�����㷨��������ʹ�õ��ǿ�Դ��linux C����qrencode��Ϊ��̬�⣬�����ɱ�����01���У���QT�Ķ�ά��ͼQPainter���ƶ�ά�롣ͬʱʹ�û���C++����Ӧ����QT��QZXing��Ϊ��̬�⣬������ͼƬ���ָ�ԭʼ��Ϣ��

#####################################################################
qrencode��Դ���ַ��http://fukuchi.org/works/qrencode/
QZXing��Դ���ַ��https://sourceforge.net/projects/qzxing/

qrencode���ɿ�ķ�����
�����ص�ѹ������ѹ��linux�¿���ֱ��ִ��./config  make  make install�������ɿ��ļ�����windows�»���linux��ֻ��Ҫ���ɱ����㷨�Ŀ⣬������Ҫlibpng��ͼƬ��������Լ�����
1) ��qrencodeԴ���е�(*.h  *.c)���뵽�����У���Ҫ��qrenc.c,��Ϊ������ʹ����png�⣬��������QPainter�Լ�������Ҫ�ÿ⣩
2) ��Դ���е�config.h.in�ļ��޸ĳ�config.h�����빤�̣���Ϊ��˾����ԭ���������������⣬��һ�����ֱ�Ӹ���չ�����ɣ�
3) ��QT��pro�ļ������DEFINES += HAVE_CONFIG_H ����ȫ�ֺ궨��
4) ���¶��� MAJOR_VERSION��MICRO_VERSION��MINOR_VERSION��VERSION
5���������ɾ�̬�⣨liaqrencodeLib.a,��Ϊ��ʹ�õ�Qt�ǻ���minGW�ģ���̬���linuxһ����.a����windows�µ�VS����.lib��
ע����Ϊʹ��qt����cԴ�뻹�������ɶ�̬�⣨.dll + .a/.lib(�˴����Ǿ�̬�⣬���Ƕ�̬��ĸ����ļ���������ʱʹ��)��������ʹ���˾�̬�⡣ʹ�øÿ�ʱ��ֻ���ڱ���pro�ļ��м���  LIBS += -L./ -lqrencodeLib ��Ȼ�����<qrencode.h>����

QZXing���ɿ�ķ�����
QZXingԴ��Ĭ��ֱ�ӹ��������ɶ�̬�⣬����QZXing2.dll��̬���libQZXing2.a�����ļ���ʹ�øÿ�ʱ��ֻ���ڱ���pro�ļ�������LIBS += -L./ -lQZXing2��Ȼ����ϡ�QZXing.h���͡�QZXing_global.h������ͷ�ļ����ɡ�����ʱĿ¼�¼��϶�̬���ļ����������ɾ�̬�⣬Ҳ�Ƚ����ף�ֻ����΢�Ķ����ɣ����qt�¾�̬���뾲̬��Ĵ�����ʹ�á�������Ŀ¼�µ�libQZXing.a���Ǿ�̬�⣩��������ʹ�õ�QZXing��̬�⣬��Ϊ��̬���Դ�

ʹ��qrencode���еķ�������ֻ��Ҫ��������Ľӿں���
QRcode *qrcode;
//QR_ECLEVEL_Q  �ݴ�ȼ�
qrcode = QRcode_encodeString("http://m.weibo.cn/u/1832088940", 2, QR_ECLEVEL_Q, QR_MODE_8, 0);
QRcode ��һ���ṹ��
typedef struct {
	int version;         ///< version of the symbol
	int width;           ///< width of the symbol
	unsigned char *data; ///< symbol data
} QRcode;
data�а��д洢�ű�����01�ַ�����1���ڿ�  0���׿�

ʹ��QZXing���еķ�������ֻ���������ķ���
QZXing *zxing;
zxing->decodeImage(image);//�÷�������QString������ʶͼƬ��ά�������

���������ṹ��
qrcodebox.cpp:���ƶ�ά��Ĳ���
qrcodewidget.cpp:�����棬���ò��������ɱ���ͼƬ������չʾ��ά��ͼƬ
qrencode.h //qrencode�⺯���ӿ�ͷ�ļ�
QZXing.h //QZXing��Ľӿں�����

#####################################################################
���˵һ��QT������windowsϵͳ�ϵĴ������
һ��������ɺ�ʹ��QT����release�汾�Ŀ�ִ��exe�ļ������ǽ���exe��ִ���ļ����޷��ڱ��˵Ļ��������еġ���ΪQTĬ���Ƕ�̬����ģ�������Ҫ���ָ����Ķ�̬���ļ����߰汾��qt��һ��windows�µĲ��𹤾�windeployqt.exe�����ɵ�release�汾��*.exe�ļ��������ŵ�һ���ļ����У���qt�������й��ߣ����߽����𹤾�����Ŀ¼��ӵ�ϵͳpath�����У�ʹ��cmd�����н���*.exe�����ļ��У�ִ������windeployqt *.exe��(*��ʾ��ĳ�����)���𹤾߻��Զ��������Ķ�̬���Լ�����ŵ��ļ����¡���ʹ�ò��𹤾�Ҳ����ֱ�ӵ��*.exe����ȱ�ٵĿ��Լ���ӣ����ڱ��������ˣ�������������ȫ���ڱ�Ļ����ϻ��޷����С���Ϊ����Ҫplugins�����һЩ�����һ����imageformats�ļ����µĸ��ָ�ʽ��ͼƬ�⣬��platform�µ�qwindows.dll������֮ȱʲôȥqt���binĿ¼��plugins���Ҿ��С�

������ϵ��ʽ��@Ϊ-��-����(����΢��)