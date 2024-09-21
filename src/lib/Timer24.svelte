<script>
    /**
     * @param {number} hr
     * @param {number} min
     * @param {number} sec
     */
    function getTimeStr(hr, min, sec, milli=0) {
        let hour_str = hr < 10 ? "0" + hr.toString() : hr.toString();
        let min_str = min < 10 ? "0" + min.toString() : min.toString();
        let sec_str = sec < 10 ? "0" + sec.toString() : sec.toString();

        let sep = ":";
        if(milli < 500) {
            sep = " ";
        }
        return hour_str + sep + min_str + sep + sec_str;
    }

    let currTime = "00:00:00";
    const showTime = () => {
        let time = new Date();
        currTime = getTimeStr(
            time.getHours(),
            time.getMinutes(),
            time.getSeconds(),
            time.getMilliseconds()
        );
    }
    showTime();
    setInterval(showTime, 500);
</script>

<h1>{currTime}</h1>
