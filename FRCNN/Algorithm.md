RPN������̣�
��ͼ�е�Proposal,ʵ���ϰ����˼�����Ҫ���̣�
1.����Ԥ���ع��Լ�����Ԥ���Ԥ���ع�ֵ��ê�����з��任����ȡԤ���ʵ������ֵ������SSD�㷨�еĽ������
2.RPN���и���Ŀ�����бȽ�ͨ�õ�˼�룬����NMS���Ǽ���ֵ���ƣ�������Ҫ��Ϊ�˱�������ж��Ԥ����Ӧһ���������������NMS�ľ���ʵ�����£�
�Ǽ���ֵ���Ƶķ����ǣ��ȼ�����6�����ο򣬸��ݷ���������������������򣬼����С�������ڳ����ĸ��� �ֱ�ΪA��B��C��D��E��F��
(1)�������ʾ��ο�F��ʼ���ֱ��ж�A~E��F���ص���IOU�Ƿ����ĳ���趨����ֵ;
(2)����B��D��F���ص��ȳ�����ֵ����ô���ӵ�B��D������ǵ�һ�����ο�F�������Ǳ��������ġ�
(3)��ʣ�µľ��ο�A��C��E�У�ѡ���������E��Ȼ���ж�E��A��C���ص��ȣ��ص��ȴ���һ������ֵ����ô���ӵ��������E�����Ǳ��������ĵڶ������ο�
������һֱ�ظ����ҵ����б����������ľ��ο�
tf�е��������£�
indices = tf.image.non_max_suppression(proposals, scores, max_output_size=post_nms_topN, iou_threshold=nms_thresh)
boxes = tf.gather(proposals, indices)
boxes = tf.to_float(boxes)
scores = tf.gather(scores, indices)
scores = tf.reshape(scores, shape=(-1, 1))

3.ROI Pooling���̣�
ROI Pooling�����������⣬���ǽ�ȡһ��ROI������Ȼ�����pool���������ǽ�ȡ�Ĳ���ԭͼ����������FM base�����õ��������㣬����������ȥ
���Ǵ����ظ��ľ���������ʵ�ֵĹؼ����� tf.image.crop_and_resize �� �����tensorflowԭ��API�����Զ�һ��tensor�����ض��Ĳü������ţ��ü�
֮�������ٽ���һ��pool

4.����ROI Pooling�󣬾�������ȫȫ���Ӳ���з���Ԥ�⼰�߿�ع飬��������㷨